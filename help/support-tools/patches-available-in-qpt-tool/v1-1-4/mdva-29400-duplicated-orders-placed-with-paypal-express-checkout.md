---
title: 'MDVA-29400: Pedidos duplicados feitos com o Check-out do PayPal Express'
description: O patch MDVA-29400 resolve o problema em que os pedidos duplicados são criados quando os clientes fazem pedidos com o Check-out do PayPal Express. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 está instalada. A ID do patch é MDVA-29400. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: Pedidos duplicados feitos com o Check-out do PayPal Express

O patch MDVA-29400 resolve o problema em que os pedidos duplicados são criados quando os clientes fazem pedidos com o Check-out do PayPal Express. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 está instalada. A ID do patch é MDVA-29400. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Pedidos duplicados são criados quando os usuários fazem pedidos com o Check-out do PayPal Express.

<u>Pré-requisitos</u>:

Finalização de compra ativada e configurada no PayPal Express.

<u>Etapas a serem reproduzidas</u>:

1. Adicionar um produto ao carrinho.
1. Vá para a Página de Finalização e use o PayPal Express como método de pagamento.
1. Ele será redirecionado para a página paypal/express/review/.
1. Fazer pedido. Você será redirecionado para a Página de sucesso.
1. Voltar para PayPal/express/review/ Page.
1. Clique no botão **Fazer pedido**.

<u>Resultados esperados</u>:

Somente uma ordem é criada.

<u>Resultados reais</u>:

Você recebe o seguinte erro: *O token de check-out do PayPal Express não existe*, mas a segunda ordem foi feita com êxito.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
