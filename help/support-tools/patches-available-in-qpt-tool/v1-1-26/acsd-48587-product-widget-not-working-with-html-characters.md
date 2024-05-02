---
title: "ACSD-48587: o widget do produto não funciona com SKUs que contêm caracteres HTML"
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

O patch ACSD-48587 corrige o problema em que caracteres especiais de HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.26 está instalado. A ID do patch é ACSD-48587. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O widget do produto não está funcionando com SKUs que contêm *&quot;&amp;&quot;* símbolos.

<u>Etapas a serem reproduzidas</u>:

1. Criar um produto contendo *&quot;&amp;&quot;* no SKU (por exemplo, s000&amp;01).
1. Edite o conteúdo de uma página CMS no *Page Builder*.
1. Adicionar um widget Produtos.
1. Editar o widget e definir **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Insira o SKU que contém *&quot;&amp;&quot;* no campo SKUs do produto.
1. Salve o conteúdo e a página do CMS.
1. Verifique a *Página CMS* conteúdo para o *Visualização do Page Builder* e loja de produtos.

<u>Resultados esperados</u>:

O produto com *&quot;&amp;&quot;* no SKU é exibido na pré-visualização do Page Builder e na loja.

<u>Resultados reais</u>:

O produto com *&quot;&amp;&quot;* no SKU não é exibido na pré-visualização do Page Builder.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
