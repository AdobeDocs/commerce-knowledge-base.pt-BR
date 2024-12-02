---
title: 'ACSD-54887: o carrinho de compras do cliente é limpo depois que a sessão do cliente expira'
description: Aplique o patch ACSD-54887 para corrigir o problema do Adobe Commerce em que o carrinho de compras do cliente é limpo depois que a sessão do cliente expira com o [!UICONTROL Persistent Shopping Cart] ativado.
feature: Shopping Cart
role: Admin, Developer
exl-id: 81e0a20e-0c68-420e-b14e-3f331249c8d9
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-54887: o carrinho de compras do cliente é limpo depois que a sessão do cliente expira

O patch ACSD-54887 corrige o problema em que o carrinho de compras do cliente é limpo depois que a sessão do cliente expira com o [!UICONTROL Persistent Shopping Cart] ativado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-54887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 e 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O carrinho de compras do cliente é limpo depois que a sessão do cliente expira com a [!UICONTROL Persistent Shopping Cart] habilitada.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar [!UICONTROL Persistent Shopping Cart]. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Sim*.

   Fazer logon com Persistência habilitada (Observação: não está disponível na autorização pop-up, mas somente na página [!UICONTROL Sign in] direta).

1. Adicione um produto ao carrinho.
1. Prossiga para o check-out e selecione um método de pagamento.
1. Expirar a sessão (excluir `PHPSESSID`).
1. Atualize a página. Observe que a cotação é imediatamente convertida em uma cotação de convidado porque um método de pagamento já está selecionado e o cookie [!UICONTROL Persistent Cart] foi removido.
1. Expirar a sessão (excluir `PHPSESSID`).
1. Atualize a página. Veja se o carrinho está vazio.
1. Entre novamente.

<u>Resultados esperados</u>:

O carrinho tem o produto quando você faz logon novamente.

<u>Resultados reais</u>:

O carrinho está vazio ao fazer logon novamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
