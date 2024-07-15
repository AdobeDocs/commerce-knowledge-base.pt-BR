---
title: O armazenamento em cache do Fastly não está funcionando no Adobe Commerce na infraestrutura da nuvem
description: Este artigo fornece uma correção para o Fastly caching não funcionar no site. O Fastly é um serviço de CDN e armazenamento em cache incluído no Adobe Commerce para planos e implementações de infraestrutura em nuvem. Para verificar se a extensão Fastly está funcionando ou para depurar a extensão Fastly, é possível usar o comando curl para exibir determinados cabeçalhos de resposta. Os valores desses cabeçalhos de resposta indicam se o Fastly está ativado e funcionando corretamente. Você pode investigar mais detalhadamente os problemas com base nos valores dos cabeçalhos e no comportamento do armazenamento em cache.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# O armazenamento em cache do Fastly não está funcionando no Adobe Commerce na infraestrutura da nuvem

Este artigo fornece uma correção para o Fastly caching não funcionar no site. O Fastly é um serviço de CDN e armazenamento em cache incluído no Adobe Commerce para planos e implementações de infraestrutura em nuvem. Para verificar se a extensão Fastly está funcionando ou para depurar a extensão Fastly, é possível usar o comando curl para exibir determinados cabeçalhos de resposta. Os valores desses cabeçalhos de resposta indicam se o Fastly está ativado e funcionando corretamente. Você pode investigar mais detalhadamente os problemas com base nos valores dos cabeçalhos e no comportamento do armazenamento em cache.

Estas informações ajudam a verificar e testar os cabeçalhos do Fastly no site ativo e nos servidores de origem.

## Versões afetadas

* Adobe Commerce na infraestrutura em nuvem
* Fastly 1.2.27 e posterior

## Problema

O armazenamento em cache pode não estar funcionando para seu site ativo, produção ou ambientes de preparo.

## Causa

Normalmente, configurações, credenciais incorretas ou extensões não compatíveis do Adobe Commerce são o problema para o Fastly caching não funcionar. Se você configurar o Fastly incorretamente ou usar uma extensão não compatível que remove cabeçalhos, o cache do Fastly não funcionará.

## Testar com comandos e verificar cabeçalhos de resposta

### Testar com comando dig

Primeiro, verifique os cabeçalhos com um comando dig para o URL. Em um aplicativo de terminal, insira dig `<url>` para verificar a exibição dos serviços do Fastly nos cabeçalhos. Para ver outros testes de pesquisa, consulte [Testes do Fastly antes de alterar o DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Por exemplo:

* Site ao vivo: `dig http[s]://<your domain>`
* Estágios: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Produção: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Testar com comando curl

Em seguida, use um comando curl para verificar se os X-Magento-Tags existem e informações adicionais do cabeçalho. O formato do comando é diferente para Preparo e Produção.

Para obter mais informações sobre esses comandos, você ignora o Fastly ao injetar `-H "host:URL"`, substituir pela origem no local de conexão (informações CNAME da Planilha do OneDrive), `-k` ignora o SSL e `-v` fornece respostas detalhadas. Se os cabeçalhos forem exibidos corretamente, verifique o site ativo e verifique os cabeçalhos novamente.

* Se ocorrerem problemas de cabeçalho ao acessar diretamente os servidores de origem sem passar pelo Fastly, você poderá ter problemas no código, com as extensões ou com a infraestrutura.
* Se você não encontrar erros ao acessar diretamente os servidores de origem, mas os cabeçalhos não estiverem acessando o domínio ativo pelo Fastly, você pode ter erros no Fastly.

Primeiro, verifique seu **site ativo** para verificar os cabeçalhos de resposta. O comando passa pela extensão Fastly para receber respostas. Se você não receber os cabeçalhos corretos, teste os servidores de origem diretamente. Este comando retorna os valores dos cabeçalhos `Fastly-Magento-VCL-Uploaded` e `X-Cache`.

1. Em um terminal, insira o seguinte comando para testar o URL do site ativo:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Use `--resolve` somente se sua URL ativa não estiver configurada com DNS e você não tiver uma rota estática definida. Por exemplo:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Verifique os cabeçalhos de resposta para garantir que o Fastly esteja funcionando. A saída desse comando é semelhante à Preparação e Produção de curl. Por exemplo, você deve ver os cabeçalhos exclusivos retornados por este comando:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Para testar **Estágios** :

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Para testar o **Balanceador de carga de produção**:

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Para testar o **nó de Origem de Produção**:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Um nó Origin direto:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Por exemplo, se você tiver um URL público www.mymagento.biz, insira um comando semelhante ao seguinte para testar o site de produção:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Verificar cabeçalhos de resposta

* Verifique os cabeçalhos e valores de resposta retornados:
* Fastly-Magento-VCL-Uploaded deve estar presente
* X-Magento-Tags deve ser retornado
* Fastly-Module-Enabled deve ser Yes ou o número de versão do Fastly extension
* O cache X deve ser HIT ou HIT, HIT
* x-cache-hits deve ser 1,1
* Cache-Control: max-age deve ser maior que 0
* O pragma deve ser armazenado em cache

O exemplo a seguir mostra os valores corretos para Pragma, X-Magento-Tags e Fastly-Module-Enabled.

A saída dos comandos curl pode ser longa. A seguir, há apenas um resumo:

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Resolver

### Fastly-Module-Enabled não está presente

Se você não receber um &quot;sim&quot; para o Fastly-Module-Enabled nos cabeçalhos de resposta, será necessário verificar se o módulo Fasty está instalado e selecionado.

Para verificar se o Fastly está ativado no ambiente de Preparo e Produção, verifique a configuração no Administrador do Commerce para cada ambiente:

1. Faça logon no Admin Console para Preparo e produção usando o URL com /admin (ou o URL de administrador alterado).
1. Navegue até Lojas > Configuração > Avançado > Sistema. Role a tela e clique em Cache de página inteira.
1. Certifique-se de que o Fastly CDN esteja selecionado.
1. Clique em Fastly Configuration. Verifique se a ID de serviço do Fastly e o token da API do Fastly foram inseridos (suas credenciais do Fastly). Verifique se você tem as credenciais corretas inseridas para o ambiente de Preparo e Produção. Clique em Testar credenciais para ajudar.
1. Edite seu composer.json e verifique se o módulo Fasty está incluído na versão. Este arquivo tem todos os módulos listados com versões.

   * Na seção &quot;require&quot;, você deverá ter o &quot;fastly/magento2&quot;: `<version number>`
   * Na seção &quot;repositórios&quot;, você deve ter:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Se você usa o Gerenciamento de configurações, deve ter um arquivo de configuração. Edite o arquivo app/etc/config.app.php (2.0, 2.1) ou app/etc/config.php (2.2) e verifique se a configuração `'Fastly_Cdn' => 1` está correta. A configuração não deve ser `'Fastly_Cdn' => 0` (o que significa desabilitado). Se você habilitou o Fastly, exclua o arquivo de configuração e execute o comando bin/magento magento-cloud:scd-dump para atualizar. Para obter uma apresentação desse arquivo, consulte [Exemplo de gerenciamento de configurações específicas do sistema](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) no Guia de Configuração.

Se o módulo não estiver instalado, você precisará instalar em uma ramificação de [Ambiente de integração](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) e implantá-lo no ambiente de preparo e produção. Consulte [Configurar Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) para obter instruções no Guia de Infraestrutura do Commerce na Nuvem.

### Fastly-Magento-VCL-Uploaded não está presente

Durante a instalação e configuração, você deve ter carregado o Fastly VCL. Estes são os trechos de VCL base fornecidos pelo módulo Fastly, não os trechos de VCL personalizados criados. Para obter instruções, consulte [Fazer upload de trechos Fastly VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) no Guia do Commerce na Infraestrutura na Nuvem.

### X-Cache inclui MISS

Se X-Cache for HIT, MISS ou MISS, MISS, insira o mesmo comando curl novamente para garantir que a página não tenha sido removida recentemente do cache.

Se você obter o mesmo resultado, use os comandos curl e verifique os cabeçalhos de resposta:

* O pragma é armazenado em cache
* X-Magento-Tags existe
* Cache-Control: max-age é maior que 0

Se o problema persistir, outra extensão provavelmente redefinirá esses cabeçalhos. Repita o procedimento a seguir no ambiente de preparo para desativar as extensões e descobrir qual delas está causando o problema. Depois de localizar as extensões que estão causando o problema, será necessário desativar as extensões na Produção.

1. Para desabilitar as extensões, siga as etapas fornecidas na seção [Gerenciar extensões](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) do guia Commerce na Infraestrutura em Nuvem.
1. Depois de desabilitar as extensões, vá para **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Clique em **[!UICONTROL Flush Magento Cache]**.
1. Agora ative uma extensão por vez, salvando a configuração e liberando o cache.
1. Experimente os comandos curl e verifique os cabeçalhos de resposta.
1. Repita as etapas 4 e 5 para ativar e testar os comandos curl. Quando os cabeçalhos do Fastly não forem mais exibidos, você terá encontrado a extensão que está causando problemas com o Fastly.

Quando você isolar a extensão que está redefinindo os cabeçalhos do Fastly, entre em contato com o desenvolvedor da extensão para obter assistência adicional. Não podemos fornecer correções ou atualizações para desenvolvedores de extensões de terceiros para trabalhar com o armazenamento em cache do Fastly.

## Mais informações em nossa documentação para desenvolvedores:

* [Sobre o Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configurar Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Snippets de VCL Fastly personalizados](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
