---
title: 'ACSD-54966: correção para reutilizar códigos de cupom após pedidos com falha'
description: Aplique o patch ACSD-54966 para corrigir o problema do Adobe Commerce, impedindo a reutilização de códigos de cupom limitados por promoções e carrinho de compras após um pedido que falhou anteriormente.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: 931cfe7a-30a3-4a7d-ada5-4e2d7084f3e1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-54966: correção para reutilizar códigos de cupom após pedidos com falha

O patch ACSD-54966 corrige o problema que impede a reutilização de códigos de cupom limitados por cliente após um pedido que falhou anteriormente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. A ID do patch é ACSD-54966. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um código de cupom, limitado para uso único por cliente, não pode ser reutilizado após um pedido anterior com falha.

<u>Etapas a serem reproduzidas</u>:

1. Configure uma regra de preço do carrinho com *[!UICONTROL Uses per Customer]* = *1*.
1. Continue fazendo uma compra usando o código de cupom atribuído.
1. Cancelar a ordem no painel de administração ou executar a ordem com falha de pagamento.
1. Execute o comando: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Tente fazer um pedido subsequente usando o mesmo código de cupom para o mesmo cliente.

<u>Resultados esperados</u>:

Depois de cancelar a ordem ou encontrar uma falha de pagamento, o cliente pode reutilizar com êxito o código do cupom para uma nova compra.

<u>Resultados reais</u>:

O cliente não pode reutilizar o código do cupom.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
