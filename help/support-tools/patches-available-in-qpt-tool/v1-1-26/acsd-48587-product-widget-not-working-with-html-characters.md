---
title: 'ACSD-48587: o widget do produto não funciona com SKUs que contêm caracteres HTML'
description: Aplique o patch ACSD-48587 para corrigir o problema do Adobe Commerce, em que os caracteres especiais de HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587: o widget do produto não funciona com SKUs que contêm caracteres HTML

O patch ACSD-48587 corrige o problema em que caracteres especiais de HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. A ID do patch é ACSD-48587. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O widget do produto não está funcionando com SKUs contendo símbolos *&quot;&amp;&quot;*.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto contendo *&quot;&amp;&quot;* na SKU (por exemplo, s000&amp;01).
1. Edite o conteúdo de uma página do CMS no *Page Builder*.
1. Adicionar um widget Produtos.
1. Edite o widget e defina **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Insira a SKU que contém *&quot;&amp;&quot;* no campo SKUs do produto.
1. Salve o conteúdo e a página do CMS.
1. Verifique o conteúdo da *Página do CMS* para a *visualização do Page Builder* e a vitrine do produto.

<u>Resultados esperados</u>:

O produto com *&quot;&amp;&quot;* na SKU é exibido na pré-visualização do Page Builder e na vitrine.

<u>Resultados reais</u>:

O produto com *&quot;&amp;&quot;* na SKU não é exibido na visualização do Page Builder.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
