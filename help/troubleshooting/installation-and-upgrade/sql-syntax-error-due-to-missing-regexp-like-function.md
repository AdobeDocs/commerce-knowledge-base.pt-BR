---
title: A atualização para B2B 1.5.2 falha com erro de sintaxe SQL devido à ausência da função REGEXP_LIKE
description: Este artigo fornece uma correção para o problema em que ocorre um erro de sintaxe SQL devido à falta da função REGEXP_LIKE ao tentar atualizar a tabela company_structure.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: f83b82a95d4592252c8923720e90733115c52d87
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# A atualização para B2B 1.5.2 falha com erro de sintaxe SQL devido à ausência da função REGEXP_LIKE

Este artigo fornece uma correção para o erro de sintaxe SQL que ocorre devido à falta da função `REGEXP_LIKE` ao tentar atualizar a tabela `company_structure`.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.4.6-px + B2B 1.5.2 usando [!DNL MariaDB] 10.6
* Adobe Commerce (todos os métodos de implantação) 2.4.7-px + B2B 1.5.2 usando [!DNL MariaDB] 10.6

## Problema

A atualização para a versão 1.5.2 B2B falha com um erro de sintaxe SQL devido à falta da função `REGEXP_LIKE` ao tentar atualizar a tabela `company_structure`.

<u>Pré-requisitos</u>:

* MariaDB 10.6
* Adobe Commerce 2.4.6x ou 2.4.7x
* Versão B2B 1.5.0 ou 1.5.1

<u>Etapas a serem reproduzidas</u>:

1. Atribua uma empresa a uma empresa principal para estabelecer a hierarquia da empresa. Consulte [Gerenciar a Hierarquia da Empresa](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) no guia B2B do Adobe Commerce para obter mais informações.
1. Atualize o B2B para a versão 1.5.2.

<u>Resultados esperados</u>:

Atualização concluída com sucesso.

<u>Resultados reais</u>:

`bin/magento setup:upgrade` falha com o seguinte erro:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Solução

Para resolver o problema, siga estas etapas:

1. Atualize o módulo B2B para a versão 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Aplique o patch [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip) anexado. Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de suporte para obter instruções.
1. Executar `bin/magento setup:upgrade`.

### Aplicar um patch usando Patches na nuvem

Para a infraestrutura do Adobe Commerce na nuvem, siga as etapas abaixo:

1. Atualize a versão do módulo `cloud-patches` para 1.1.5:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Confirme e envie as alterações para iniciar a reimplantação. Consulte [Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) em nosso guia do Adobe Commerce na nuvem para obter instruções.
