---
title: 'Falha na implantação com "Erro ao criar projeto: o gancho de criação falhou com o código de status 1"'
description: 'Este artigo fala sobre as causas e soluções do problema de infraestrutura na nuvem do Adobe Commerce, em que a fase de criação do processo de implantação falha, e a mensagem de erro é resumida com: *"Error building project: The build hook failed with status code 1"*.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Falha na implantação com &quot;Erro ao criar projeto: o gancho de criação falhou com o código de status 1&quot;

Este artigo fala sobre as causas e soluções do problema de infraestrutura na nuvem do Adobe Commerce, em que a fase de compilação do processo de implantação falha, e a mensagem de erro é resumida com: *&quot;Erro ao compilar o projeto: O gancho de compilação falhou com o código de status 1&quot;*.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

<u>Etapas a serem reproduzidas</u>:

Acione a implantação manualmente ou executando uma mesclagem, push ou sincronização do seu ambiente.

<u>Resultado esperado</u>:

A implantação foi concluída com êxito.

<u>Resultado real</u>:

1. A fase de criação falha e todo o processo de implantação fica paralisado.
1. No log de erros de implantação, a mensagem de erro termina com: *&quot;Projeto de compilação de erro: falha do gancho de compilação com o código de status 1. Compilação anulada&quot;.*

## Causa

Há vários motivos pelos quais a criação de ambientes falha. Normalmente, no log de implantação, você verá uma mensagem de erro longa, em que a primeira parte seria mais específica em relação ao motivo, e a conclusão seria *&quot;Erro ao compilar o projeto: o gancho de compilação falhou com o código de status 1. Compilação anulada&quot;.*

Analisar de perto a primeira parte específica do problema ajudará você a identificar o problema. Estas são as mais comuns e a próxima seção fornece soluções para elas:

* Não há espaço de armazenamento disponível.
* Configuração ECE-Tools incorreta.
* O patch que você está tentando aplicar é incompatível com sua versão do Adobe Commerce ou está em conflito com outros patches aplicados ou com suas personalizações.
* Problemas com o código de módulos personalizados estão impedindo a criação com êxito.

## Solução

* Verifique se há armazenamento suficiente. Para obter informações sobre como verificar o espaço disponível, consulte o artigo [Verificar espaço em disco no ambiente de nuvem usando a CLI](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md). Você pode considerar limpar os diretórios de log e/ou aumentar o espaço em disco.
* Verifique se as ECE-Tools estão configuradas corretamente.
* Verifique se é o patch que está causando o problema. Resolva o conflito ou contate o [Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consulte abaixo para obter detalhes.
* Verifique se é a extensão personalizada que está causando o problema. Resolva o conflito ou entre em contato com os desenvolvedores de extensão para obter a solução.

Os parágrafos a seguir fornecem mais detalhes.

### Limpar logs e/ou aumentar espaço

Diretórios a serem considerados para limpeza:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Para obter detalhes sobre como aumentar o espaço em disco se você estiver na arquitetura de plano inicial do Adobe Commerce na infraestrutura de nuvem, consulte o [Aumentar espaço em disco para o ambiente de Integração na nuvem](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). As mesmas instruções podem ser usadas para aumentar o espaço do Adobe Commerce no ambiente de integração da arquitetura de plano Pro da infraestrutura em nuvem. Para Produção/Preparo Profissional, você precisa registrar um tíquete no [Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e solicitar mais espaço em disco. Mas é monitorado pela Platform. Mas, normalmente, você não precisará lidar com isso na arquitetura Preparação/Produção da Pro, pois o Adobe Commerce monitora esses parâmetros para você e o alerta e/ou executa ações de acordo com o contrato.

### Verifique se as ferramentas ECE estão configuradas corretamente

1. Verifique se os ganchos de compilação estão definidos corretamente no arquivo `magento.app.yaml`. Se você estiver no Adobe Commerce 2.2.X, os ganchos de construção deverão ser definidos da seguinte maneira:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Use o artigo [Atualizar para ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) para referência.

1. Verifique se o pacote ECE-tools está presente no arquivo `composer.lock` executando o seguinte comando:    <pre><code class="language-bash">grep &#39;<code class="language-yaml">&quot;name&quot;: &quot;magento/ece-tools&quot;</code>&#39; composer.lock</code></pre>    Se forem especificados, a resposta será semelhante ao seguinte exemplo:    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

Consulte o artigo [Atualizar para ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) para referência.

### O patch está causando o problema?

Se for o patch aplicado que está impedindo o ambiente de ser criado com sucesso, você verá algo semelhante ao seguinte no log de implantação:

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Essas mensagens de erro significam que o patch que você está tentando aplicar foi criado para uma versão diferente do Adobe Commerce ou está em conflito com suas personalizações ou patches aplicados anteriormente. Tente resolver o conflito ou contate o [Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### A extensão está causando o problema?

Se for a extensão personalizada que está impedindo o ambiente de ser criado com sucesso, você verá os nomes dos módulos personalizados mencionados no log de implantação, juntamente com o conflito específico causado por esse módulo. Resolva o conflito ou entre em contato com os desenvolvedores de extensão para obter a solução.

### Verifique se as alterações foram aplicadas

Confirme e envie suas alterações. Isso acionará a implantação automaticamente.
