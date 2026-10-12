---
title: O site na nuvem está lento
description: Este artigo fornece recomendações sobre como melhorar o desempenho do seu Adobe Commerce no site de infraestrutura em nuvem com cargas de tráfego pesado e como reduzir essa carga.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%
---
# O site na nuvem está lento

Este artigo fornece recomendações sobre como melhorar o desempenho do seu Adobe Commerce no site de infraestrutura em nuvem com cargas de tráfego pesado e como reduzir essa carga.

## Versões e edições afetadas

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

<u>Etapas a serem reproduzidas</u>

1. Visite sua loja da Adobe Commerce.
1. Navegar em uma página de categoria.
1. Adicione um produto ao carrinho.

<u>Resultado esperado</u>

O site é responsivo e adicionar um produto ao carrinho é rápido.

<u>Resultado real</u>

O site está lento ou as páginas de categoria são rápidas, mas a página do carrinho está lenta.

## Etapas e soluções de depuração

Execute as seguintes etapas para rastrear o motivo do desempenho lento e corrigi-lo. Você pode alternar a primeira e a segunda etapas, mas prosseguir para o bloqueio de IPs somente se a otimização das configurações de cache não ajudar.

1. Verifique a taxa de ocorrência do cache para as páginas com alto tráfego e reduza a quantidade de dados altamente atualizados.
1. Verifique a taxa geral de acertos do cache do site e a configuração geral do cache/Fastly.
1. Identifique os clientes da Web que estão causando a carga alta do servidor e bloqueie os IPs que estão causando a carga alta.

Os parágrafos a seguir fornecem mais detalhes para cada etapa.

### Etapa 1: verifique a taxa de ocorrência do cache para as páginas com alto tráfego

A primeira etapa para corrigir um site atolado em tráfego pesado é garantir que as páginas com o tráfego mais pesado, como a página inicial da loja e as páginas de categoria de nível superior, estejam sendo armazenadas em cache corretamente.

Você pode descobrir as taxas de ocorrência do cache para essas páginas revisando os `X-Cache` cabeçalhos HTTP usando cURL, conforme descrito em [Verificando o cache usando cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) na documentação do Fastly. Ou verifique os mesmos cabeçalhos usando a guia Rede na barra de ferramentas do desenvolvedor do seu navegador da Web favorito.

O Fastly geralmente respeita os cabeçalhos de resposta provenientes do aplicativo; no entanto, se os cabeçalhos estiverem definidos como &quot;não armazenar em cache&quot; e para a página &quot;expirar no passado&quot;, o Fastly não poderá armazenar a página em cache.

>[!WARNING]
>
>Observe que o Fastly altera os cabeçalhos de resposta, portanto, verificar o URL principal com cURL ou o navegador da web não mostrará necessariamente quais cabeçalhos estão sendo emitidos pelo aplicativo. É comum que o próprio Fastly responda a navegadores da Web com cabeçalhos &quot;sem cache&quot;, mas que o próprio aplicativo da Web permita o armazenamento em cache e que o Fastly armazene o item em cache corretamente. Portanto, as informações dos cabeçalhos &quot;cache-control&quot; e &quot;pragma&quot; não serão úteis nesse caso.

#### Solução de problemas para páginas com alto tráfego

Se a página de índice tiver uma taxa de ocorrência baixa, você poderá corrigi-la reduzindo a quantidade de dados altamente atualizados presentes nessa página.

### Etapa 2: verificar a taxa geral de acertos do cache do site

Para verificar a taxa geral de acertos do cache:

1. [Obtenha credenciais do Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration) para seu Adobe Commerce no ambiente de infraestrutura na nuvem.
1. Execute o seguinte comando cURL do Linux/macOS para verificar a taxa de ocorrência do site nos últimos 30 minutos, substituindo e pelos valores das credenciais do Fastly:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Você também pode verificar o histórico das taxas de ocorrência no último dia ou mês alterando a opção de consulta de intervalo de tempo de `?by=minute` para `?by=hour` ou `?by=day`. Para obter mais informações sobre como obter as estatísticas do cache do Fastly, consulte [Opções de Consulta](https://docs.fastly.com/api/stats#Query) na documentação do Fastly.

   A opção `| json_pp` imprime a saída da resposta JSON usando o utilitário `json_pp`. Se você receber um erro _&#39;json\_pp not found&#39;_, instale o utilitário `json_pp` ou use outra ferramenta de linha de comando para obter uma impressão JSON. Como alternativa, exclua o parâmetro `| json_pp` e execute o comando novamente. A saída da resposta JSON não está formatada, mas você pode executá-la por meio de um beautificador JSON para limpá-la.

Uma taxa de ocorrência acima de 0,90 ou 90% indica que o cache de página inteira está funcionando.

Uma taxa de ocorrência abaixo de 0,85 ou 85% pode indicar um problema de configuração do site ou você pode ter uma extensão de terceiros instalada que não permite que o conteúdo seja armazenado em cache.

#### Solução de problemas da taxa geral de acertos do cache

1. Usando as estatísticas de taxa de ocorrência por hora e por dia, identifique quando a taxa de ocorrência começou a diminuir. Se a taxa de ocorrência cair repentinamente ao mesmo tempo em que você implantou uma alteração no site, considere reverter a alteração até que o carregamento do site diminua.
1. Verifique a configuração no Administrador do Commerce, em **Lojas** > **Configuração** > Avançado > **Sistema** > **Cache de Página Inteira**. Verifique se o valor de **TTL para conteúdo público** não está definido como muito baixo.
1. Verifique se você [carregou os trechos de VCL](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Se você usar trechos de VCL personalizados, depure-os para o uso correto das ações &quot;passar&quot; ou &quot;pipe&quot;: eles devem ser usados com cuidado e, no mínimo, usados com algum tipo de condição. Para obter mais dicas, consulte [Custom Fastly VCL snippets](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) na documentação do desenvolvedor.

### Etapa 3: identificar os sites que causam a alta carga do servidor

Você pode usar qualquer um dos métodos a seguir para obter informações sobre os endereços IP que acessam sua loja da Adobe Commerce.

* Verifique os logs de acesso HTTP por meio de uma sessão SSH.
* Entre em contato com o suporte da Adobe Commerce para solicitar uma lista de endereços IP que causam grande carga no site.

#### Verificar os logs de acesso HTTP

Para exibir o log de acesso do site, execute o seguinte comando no ambiente de desenvolvimento local:

```bash
magento-cloud log access
```

Exibir mais linhas com o

```bash
--lines
```

, por exemplo:

```bash
magento-cloud log access --lines=500
```

Você pode visualizar esse log e verificar se uma grande parte das solicitações vem de um endereço IP específico. Outra maneira é usar o `awk`, `sort` e `uniq` para contar automaticamente os endereços IP mais frequentes no log, como o seguinte:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Se a variável

```bash
magento-cloud log
```

comando não funciona, você pode se conectar ao servidor remoto com SSH e verificar o arquivo de log em `/var/log/access.log`

Depois de identificar os endereços IP que estão causando grande carga no servidor, você pode bloqueá-los configurando uma lista de bloqueios de IP no painel Administrador do Commerce, em **Lojas** > **Configuração** > AVANÇADO > **Sistema** > **Cache de Página Inteira** > **Configuração Rápida** > **Bloqueio**.

Se não conseguir acessar o Administrador devido à grande carga, você poderá usar a API do Fastly para configurar as regras de bloqueio:

1. Crie a ACL conforme descrito no documento [Trabalho com ACLs usando a API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) do Fastly.
1. Na seção `recv`, crie um trecho de VCL com o seguinte conteúdo, tendo substituído ACL\_NAME\_GOES\_HERE pelo nome da ACL criada na etapa anterior:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Para obter mais informações sobre o bloqueio de endereços IP, consulte o [Guia do módulo do Fastly Adobe Commerce](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) no GitHub.
