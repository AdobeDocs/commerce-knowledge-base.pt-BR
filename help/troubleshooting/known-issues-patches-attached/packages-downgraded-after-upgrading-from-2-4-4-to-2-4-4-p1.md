---
title: Pacotes rebaixados após a atualização de 2.4.4 para 2.4.4-p1
description: Este artigo fornece um hotfix para o problema quando os comerciantes na versão 2.4.4 executam o comando "composer update" e, em seguida, os pacotes (módulos) listados abaixo são rebaixados para suas versões anteriores que não são compatíveis com a versão 2.4.4 e só devem ser usados com a versão 2.4.5 e superior.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Pacotes rebaixados após a atualização de 2.4.4 para 2.4.4-p1

Este artigo fornece uma correção para o problema que ocorria quando os comerciantes na versão 2.4.4 executavam a `composer update` e, em seguida, os pacotes (módulos) listados abaixo estão sendo rebaixados para suas versões anteriores que não são compatíveis com a versão 2.4.4 e só devem ser usadas com a versão 2.4.5 e superior.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.4
* Adobe Commerce no local 2.4.4
* Magento Open Source 2.4.4

## Problema

Há dois cenários para a ocorrência desse problema e como ele pode ser reproduzido:

### Cenário 1

<u>Etapas a serem reproduzidas</u>:

Ao atualizar da versão 2.4.4 para a 2.4.4-p1, há vários pacotes (módulos) que são rebaixados com saída semelhante:

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>Resultados esperados</u>:

A atualização da versão 2.4.4 para 2.4.4-p1 resulta nos pacotes (módulos) corretos para a versão 2.4.4-p1.

<u>Resultados reais</u>:

Durante a atualização da versão 2.4.4 para 2.4.4-p1, as versões desses pacotes (módulos) são submetidas a downgrade, mas essas mensagens podem ser ignoradas e a funcionalidade não é afetada.

### Cenário 2

<u>Etapas a serem reproduzidas</u>:

Quando os comerciantes do 2.4.4 executam o `composer update` e, em seguida, os mesmos pacotes (módulos) listados acima em **Cenário 1** atualize para as versões mais recentes, que são compatíveis somente com a versão 2.4.5 e não devem ser usadas com a versão 2.4.4.

<u>Resultados esperados</u>:

A atualização da versão 2.4.4 para 2.4.4-p1 resulta nos pacotes (módulos) corretos para a versão 2.4.4-p1.

<u>Resultados reais</u>:

Os pacotes (módulos) são rebaixados após a atualização da versão 2.4.4 para a 2.4.4-p1.

## Solução 1: Patch

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir: [Baixar ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## Versões compatíveis do Adobe Commerce e Magento Open Source:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.4.4
* Adobe Commerce no local 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>O patch não é compatível com nenhuma outra versão e edição do Adobe Commerce e Magento Open Source.

## Como aplicar o patch

Usar o script bash anexado [ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip) como solução alternativa para esse problema.

**Instruções exatas sobre como usar o script:**

### No Adobe Commerce sobre infraestrutura em nuvem:

1. Baixar o arquivo de script bash `ACPLTSRV-2017-fix.sh` para o check-out local da base de código de nuvem.
1. Execute o arquivo de script bash `ACPLTSRV-2017-fix.sh` para modificar os arquivos do compositor localmente.
1. Adicione e confirme os arquivos do compositor modificados no repositório Git.

### No Adobe Commerce ou Magento Open Source no local:

1. Coloque o script bash `ACPLTSRV-2017-fix.sh` no `root` pasta da sua instalação do Adobe Commerce/Magento Open Source 2.4.4 (a mesma pasta da `composer.json`).
1. Execute o script bash com um `apply` argumento para bloquear pacotes afetados (módulos) às suas versões 2.4.4:

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Execute o composer atualizado para instalar os pacotes bloqueados (módulos).
1. Quando estiver pronto para atualizar para 2.4.5 ou 2.4.4-p1, execute o script com um `rollback` argumento:

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Ignorar esta etapa resultará em erros de atualização devido a requisitos de pacotes (módulos) conflitantes.
1. Após a conclusão das etapas acima, você pode começar a atualização.

## Solução alternativa 2

A 2ª solução alternativa para esse problema é não executar o `composer update` comando sem nenhum argumento.
