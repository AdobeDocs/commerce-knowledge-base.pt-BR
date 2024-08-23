---
title: "ACSD-56979: imagens do produto removidas após a exclusão da atualização de preparo"
description: Aplique o patch ACSD-56979 para corrigir o problema do Adobe Commerce em que as imagens do produto são removidas após excluir uma atualização de preparo
feature: Products
role: Admin, Developer
source-git-commit: e97850bcaa98b1ccc1522fb6ee0046cd38bf1c93
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-56979: imagens do produto removidas após a exclusão da atualização de preparo

O patch ACSD-56979 corrige o problema em que as imagens do produto são removidas após excluir uma atualização de preparo. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 está instalado. A ID do patch é ACSD-56979. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce e do Magento Open Source:**

* Adobe Commerce (todos os métodos de implantação) >=2.4.3 &lt;2.4.7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens do produto são removidas após a exclusão de uma atualização de preparo.

<u>Etapas a serem reproduzidas</u>:

1. Na barra lateral do Administrador do Commerce, vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crie um produto.
1. Em **[!UICONTROL Images and Videos]**, carregue uma imagem e salve o produto.
1. Na caixa **[!UICONTROL Scheduled Changes]**, selecione **[!UICONTROL Schedule New Update]**.
   1. Escolha uma data de início de alguns minutos no futuro.
   1. Não escolha uma data final.
1. Na caixa **[!UICONTROL Scheduled Changes]**, selecione o link **[!UICONTROL View/Edit]**.
1. Vá para **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** e selecione **[!UICONTROL Done]**.
1. Atualize a página.

<u>Resultados esperados</u>:

Como a atualização é removida antes da data de início agendada, o produto deve permanecer o mesmo.

<u>Resultados reais</u>:

O conteúdo da imagem é perdido e mostra zero bytes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
