---
title: "ACSD-55427: um administrador não pode cancelar a atribuição do produto de **[!UICONTROL Product in Shared Catalogs]** na página do produto"
description: Aplique o patch ACSD-55427 para corrigir o problema do Adobe Commerce em que um produto não pode ser desatribuído do **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: um administrador não pode cancelar a atribuição do produto do **[!UICONTROL Product in Shared Catalogs]** na página do produto

O patch ACSD-55427 corrige o problema em que não é possível cancelar a atribuição de um produto do **[!UICONTROL Product in Shared Catalogs]** na página do produto no catálogo do Administrador do Commerce. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.44 está instalado. A ID do patch é ACSD-55427. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Não é possível cancelar a atribuição de um produto a **[!UICONTROL Product in Shared Catalogs]** na página do produto no catálogo do Administrador do Commerce.

<u>Etapas a serem reproduzidas</u>:

Pré-requisitos: Adobe Commerce instalado com B2B e **[!UICONTROL Shared Catalogs]** ativado.
1. Crie um produto.
1. Navegue até o painel do catálogo compartilhado e abra o catálogo compartilhado padrão.
1. Atribuir o produto ao catálogo padrão e definir um preço inferior ao preço do produto.
1. Salve o catálogo compartilhado.
1. Execute o [!UICONTROL CRON] para atualizar os consumidores/indexadores.
1. Abra o produto e remova-o do em **[!UICONTROL Product in Shared Catalogs]** seção.

<u>Resultados esperados</u>:

O produto deve ser removido de em **[!UICONTROL Product in Shared Catalogs]** seção.

<u>Resultados reais</u>:

O produto ainda é exibido no **[!UICONTROL Product in Shared Catalogs]** seção.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
