---
title: Falha na implantação com as chaves de acesso corretas em env:COMPOSER_AUTH ou auth.json
description: 'Este artigo fornece uma solução para o problema em que a implantação falha com o seguinte erro: "The https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip file could not be downloaded (HTTP/1.1 404 Not Found)".'
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 2a1c97c65282d03010bffabbcd2d1be7fb9ff9a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Falha na implantação com as chaves de acesso corretas em env:COMPOSER_AUTH ou auth.json

Este artigo fornece uma solução para o problema que ocorre quando a implantação falha com um erro como o mostrado abaixo, no [log de implantação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.x

## Problema

<u>Etapas a serem reproduzidas</u>:

Tentativa de implantação.

<u>Resultados esperados</u>:

Implantação bem-sucedida.

<u>Resultados reais</u>:

>[!NOTE]
>
>Este é um exemplo de erro. Você pode receber um erro indicando um arquivo diferente (dependendo da versão do Adobe Commerce implantada).

Você não implantou o com sucesso. Você vê um erro como *Não foi possível baixar o arquivo &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; (HTTP/1.1 404 Não encontrado)* no [log de implantação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

### Causa

As chaves de acesso do compositor especificadas encontradas em um desses locais podem não ter acesso ao código:

* na variável `env:COMPOSER_AUTH` no nível do projeto
* no `auth.json file`, que tem precedência sobre a variável `env:COMPOSER_AUTH`.

### Solução

Atualize a variável `env:COMPOSER_AUTH` no nível do projeto e verifique se ela está configurada com chaves que têm acesso ao código.

Para ver as etapas, consulte [Níveis de variáveis](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) no Guia de Infraestrutura do Commerce na Nuvem.

## Leitura relacionada

* [O Adobe Commerce no repositório de nuvem não pôde ser acessado: erro 403 proibido ou 404 não encontrado ao implantar](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Erro de implantação: erro 7 ao baixar ... porta 443: conexão recusada](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
