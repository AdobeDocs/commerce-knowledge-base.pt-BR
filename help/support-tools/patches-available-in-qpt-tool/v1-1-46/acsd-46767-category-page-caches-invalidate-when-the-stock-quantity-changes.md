---
title: '"ACSD-46767: [!UICONTROL Category] os caches de página são invalidados quando a quantidade de estoque é alterada'
description: Aplique o patch ACSD-46767 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Category] os caches de página são invalidados quando a quantidade em estoque é alterada, mesmo que o produto ainda esteja em estoque.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] os caches de página são invalidados quando a quantidade de estoque é alterada

O patch ACSD-46767 corrige o problema em que o [!UICONTROL Category] os caches de página são invalidados quando a quantidade em estoque é alterada, mesmo que o produto ainda esteja em estoque. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.46 está instalado. A ID do patch é ACSD-46767. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!UICONTROL Category] os caches de página são invalidados quando a quantidade de estoque é alterada.

<u>Etapas a serem reproduzidas</u>:

1. Crie alguns produtos e adicione-os à mesma categoria.
1. Abra o *[!UICONTROL Category]* na loja para garantir que a página seja armazenada em cache.
1. Colocar o pedido com um dos produtos da categoria *(a quantidade do produto é alterada, mas o produto ainda está em estoque)*.
1. Abra o [!UICONTROL Category] página na loja novamente.

<u>Resultados Reais</u>:

A página não é carregada do cache. Ela é gerada novamente.

<u>Resultados esperados</u>:

A página é carregada do cache.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
