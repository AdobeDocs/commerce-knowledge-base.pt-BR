---
title: Problema de desempenho na atualização do módulo Magento_Company após a atualização B2B 1.5.2
description: Este artigo fornece uma hotfix para o problema de desempenho na atualização do módulo Magento_Company após a atualização B2B 1.5.2, abordando o tempo de processamento excessivamente longo para conjuntos de dados grandes na tabela company_structure.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Problema de desempenho na atualização do módulo Magento_Company após a atualização B2B 1.5.2

Este artigo fornece uma hotfix para o problema de desempenho na atualização do módulo `Magento_Company` após a atualização B2B 1.5.2, abordando o tempo de processamento excessivamente longo para conjuntos de dados grandes (aproximadamente 100.000+ registros) na tabela `company_structure`.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (todos os métodos de implantação) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (todos os métodos de implantação) 2.4.8 + B2B 1.5.2

## Problema

A atualização do módulo `Magento_Company` após a atualização para B2B 1.5.2 leva um tempo excessivamente longo ao processar um grande número de registros (~100.000+) na tabela `company_structure`.

<u>Pré-requisitos</u>:

* ACSD-65540_B2B_1.5.2.patch deve ser instalado.
* Adobe Commerce 2.4.6 - 2.4.8
* B2B versão 1.5.0, 1.5.1 ou B2B 1.5.2 com o patch ACSD-65540 aplicado

<u>Etapas a serem reproduzidas</u>:

1. Atribua uma empresa a uma empresa principal para estabelecer a hierarquia da empresa. Consulte [Gerenciar a Hierarquia da Empresa](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) no guia B2B do Adobe Commerce para obter mais informações.
1. Atualize o B2B para a versão 1.5.2.

<u>Resultados esperados</u>:

Atualização concluída com sucesso.

<u>Resultados reais</u>:

A atualização do módulo `Magento_Company` demora para ser concluída se houver muitos registros na tabela `company_structure`.

## Solução

Para resolver o problema, siga estas etapas:

1. Atualize o módulo B2B para a versão 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Aplicar o [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip).

1. Aplique o [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) anexado.
1. Execute `bin/magento setup:upgrade` após aplicar o patch.

### Como aplicar o patch

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) em nossa base de dados de suporte para obter instruções.

### Aplicar um patch usando Patches na nuvem

Para comerciantes do Adobe Commerce on Cloud, siga as etapas abaixo:

1. Atualize a versão do módulo de patches de nuvem para 1.1.5 para instalar o ACSD-65540_B2B_1.5.2.patch distribuído como MCLOUD-13605.

   >[!NOTE]
   >
   >Para verificar se o patch já está instalado, execute:
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Adicione o patch ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2 ao diretório `m2-hotfixes`.
1. Confirme e envie por push as alterações para iniciar a reimplantação e `bin/magento setup:upgrade`. Consulte [Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) em nosso guia do Adobe Commerce na nuvem para obter instruções.

## Leitura relacionada

* [Falha na atualização para B2B 1.5.2 com erro de sintaxe SQL devido à ausência da função REGEXP_LIKE](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
