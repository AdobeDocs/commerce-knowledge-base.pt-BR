---
title: 'ACSD-51700: erro ao alternar exibições da loja na página de edição do produto baixável'
description: Aplique o patch ACSD-51700 para corrigir o problema do Adobe Commerce em que ocorre um erro ao alternar as exibições da loja em uma página de edição de produto baixável no administrador.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: erro ao alternar exibições da loja na página de edição do produto baixável

O patch ACSD-51700 corrige o problema em que ocorre um erro ao alternar as exibições da loja em uma página de edição de produto baixável no administrador. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51700. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

## Problema

Ocorre um erro ao alternar as exibições da loja em uma página de edição de produto baixável no administrador.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto para download com um nome, [!DNL SKU] e preço. Não adicione nenhum link e salve o produto.
1. Alternar de todas as exibições de loja para a exibição de loja padrão.
1. Crie um link para o produto baixável e salve-o.
1. Alternar da exibição de armazenamento padrão para todas as exibições de armazenamento.

<u>Resultados esperados</u>:

Os produtos vinculados estão visíveis.

<u>Resultados reais</u>:

O seguinte erro é exibido:

*Funcionalidade obsoleta: number_format(): passar nulo para o parâmetro #1 ($num) do tipo float está obsoleto em vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php na linha 228*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
