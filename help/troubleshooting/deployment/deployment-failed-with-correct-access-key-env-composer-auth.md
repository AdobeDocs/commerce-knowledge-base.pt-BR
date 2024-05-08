---
title: "Falha na implantação com as chaves de acesso corretas em env:COMPOSER_AUTH ou auth.json"
description: 'Este artigo fornece uma solução para o problema em que a implantação falha com o seguinte erro: "The https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip file could not be downloaded (HTTP/1.1 404 Not Found)".'
feature: Deploy
role: Admin
source-git-commit: 8e0aca8f528b017e288ae6fb19b072a5cc04761b
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Falha na implantação com as chaves de acesso corretas em env:COMPOSER_AUTH ou auth.json

Este artigo fornece uma solução para o problema que ocorre quando a implantação falha com um erro como o mostrado abaixo, na [log de implantação](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

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

Você não implantou o com sucesso. Você vê um erro como *O arquivo &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; não pôde ser baixado (HTTP/1.1 404 Não encontrado)* no [log de implantação](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).


### Causa

As chaves de acesso do compositor especificadas encontradas em um desses locais podem não ter acesso ao código:

* no `env:COMPOSER_AUTH` no nível do projeto
* no `auth.json file`, que tem precedência sobre o `env:COMPOSER_AUTH` variável.

### Solução

Atualize o `env:COMPOSER_AUTH` no nível do projeto e verifique se ela está configurada com chaves que têm acesso ao código.

Para obter etapas, consulte [Níveis variáveis](/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) no Guia de infraestrutura do Commerce na nuvem.

## Leitura relacionada

* [O Adobe Commerce no repositório de nuvem não pôde ser acessado: erro 403 proibido ou 404 não encontrado ao implantar](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Erro de implantação: erro 7 ao baixar ... porta 443: conexão recusada](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/deployment-error-downloading-connection-refused-adobe-commerce.html)
