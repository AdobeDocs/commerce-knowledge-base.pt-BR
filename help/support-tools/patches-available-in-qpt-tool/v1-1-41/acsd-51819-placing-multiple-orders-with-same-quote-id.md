---
title: "ACSD-51819: Fazer vários pedidos com uma ID de cotação única"
description: Aplique o patch ACSD-51819 para corrigir o problema do Adobe Commerce em que vários pedidos podem ser feitos por meio da mesma ID de cotação.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: Fazer vários pedidos com uma ID de cotação única

O patch ACSD-51819 corrige o problema em que vários pedidos podem ser feitos por meio da mesma ID de cotação. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.41 está instalado. A ID do patch é ACSD-51819. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Vários pedidos podem ser feitos com a mesma ID de cotação.

<u>Etapas a serem reproduzidas</u>:

1. Efetue logon como usuário.
1. Adicione itens ao carrinho e prossiga para o check-out.
1. Escolha qualquer método de pagamento, mas não clique no **[!UICONTROL Place Order]** botão.
1. Faça logon na mesma conta em outro navegador.
1. Prossiga para o check-out com os mesmos itens sem clicar no ícone **[!UICONTROL Place Order]** botão.
1. Clique no link **[!UICONTROL Place Order]** em ambos os sistemas ao mesmo tempo.
1. Validar os pedidos feitos em ambos os navegadores.

<u>Resultados esperados</u>:

Somente o primeiro pedido feito de um navegador é processado com êxito.

<u>Resultados reais</u>:

Foram feitos pedidos em ambos os navegadores.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
