---
title: 'ACSD-51230: a conta do cartão-presente é excluída'
description: Aplique o patch ACSD-51230 para corrigir o problema do Adobe Commerce em que a conta de cartão-presente é excluída quando o reembolso parcial de um produto simples é processado a partir de um pedido.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230: a conta do cartão-presente é excluída

O patch ACSD-51230 corrige o problema em que a conta do cartão-presente é excluída quando o reembolso parcial de um produto simples é processado a partir de um pedido. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-51230. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A conta do cartão-presente é excluída quando o reembolso parcial de um produto simples é processado de um pedido.

<u>Etapas a serem reproduzidas</u>:

1. Crie um pedido com um *Cartão-presente* e um *produto simples* (por exemplo, *adicione: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (qualquer método de pagamento e envio funciona).
1. Faturar a ordem.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Uma conta é criada para o cartão-presente.
1. Agora vá para **[!UICONTROL Order]** e crie um **[!UICONTROL Credit Memo]**.
1. Altere a quantidade do *Cartão-presente* para 0 e atualize-a. Isso criará um reembolso parcial para o *produto simples*.
1. Clique em **[!UICONTROL Refund]**.
1. Atualize agora o **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. A conta recém-criada é excluída.

<u>Resultados esperados</u>

A conta do cartão-presente está disponível para uso, pois o reembolso não foi criado para o cartão-presente.

<u>Resultados reais</u>

A conta do cartão-presente é excluída e o cartão-presente não é reembolsado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
