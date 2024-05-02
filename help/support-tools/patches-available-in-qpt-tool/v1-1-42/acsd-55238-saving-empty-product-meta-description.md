---
title: "ACSD-55238: Salvar a metadescrição do produto vazia"
description: Aplique o patch ACSD-55238 para corrigir o problema do Adobe Commerce em que uma descrição de produto que contém o código HTML gerado pelo [!DNL Page Builder] ou outro editor de HTML é sempre exibido na meta descrição e não há como defini-la como empty.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: Salvar a metadescrição vazia do produto

O patch ACSD-55238 corrige o problema em que uma descrição de produto contendo código de HTML gerado por um editor de HTML é sempre exibida na metadescrição. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.42 está instalado. A ID do patch é ACSD-55238. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma descrição de produto que contém o código HTML gerado por [!DNL Page Builder] ou outro editor de HTML é sempre exibido na meta descrição e não há como defini-la como empty.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** e crie um novo bloco com qualquer conteúdo.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** e criar um novo produto. Defina a meta descrição como empty.
1. Adicione o bloco criado acima usando *[!DNL Page Builder]* no *[!UICONTROL Content]* e salve o produto.
1. Abra o produto na loja e verifique seu elemento de documento `meta name = "description"`.

<u>Resultados esperados</u>:

A meta descrição está vazia.

<u>Resultados reais</u>:

Quando um produto tem um bloco em sua descrição, ele é usado para a metadescrição do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
