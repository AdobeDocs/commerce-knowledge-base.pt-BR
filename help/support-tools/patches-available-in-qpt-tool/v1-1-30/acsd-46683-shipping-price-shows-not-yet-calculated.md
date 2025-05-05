---
title: 'ACSD-46683: preço de envio mostra *Ainda não calculado*'
description: Aplique o patch ACSD-46683 para corrigir o problema do Adobe Commerce em que o preço de envio mostra *Ainda não calculado*.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: O preço de envio mostra *Ainda não calculado*

O patch ACSD-46683 corrige o problema em que o preço de envio mostra *Ainda não calculado*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. A ID do patch é ACSD-46683. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O preço de envio mostra *Ainda não calculado*.

<u>Pré-requisitos</u>:

Os módulos Adobe Commerce Inventory management (MSI) são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples e defina seu preço como *$34*.
1. Configure o método de delivery de frete grátis.
1. Configure pelo menos mais um método de delivery.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** e crie uma nova regra:
   * Nome = *75more*
   * Cupom = Nenhum
   * Prioridade = 1
   * Condições: Subtotal é igual ou maior que *$75*
   * Ações:
      * Aplicar à Quantia de Entrega = Sim
      * Descartar regras subsequentes = Não
      * Frete Livre = Para entregas com itens correspondentes
1. Crie outra regra de preço de carrinho:
   * Nome = *35off*
   * Prioridade = 0
   * Cupom = Cupom Específico
   * Código do cupom = 35off
   * Ações:
      * Aplicar = Percentual de desconto de preço do produto
      * Quantia de Desconto = 35
      * Aplicar à Quantia de Entrega = Não
      * Descartar regras subsequentes = Sim
      * Frete Gratuito = Não
1. Abra a loja e adicione três produtos ao carrinho para que o subtotal exceda US$ 75.
1. Prossiga para o check-out como convidado.
1. Na etapa de envio, selecione **$0 - envio gratuito** e prossiga para a etapa de pagamento.
1. Verifique o [!UICONTROL Order Summary] na etapa de pagamento. Ele mostra *[!UICONTROL $0 - Free Shipping - Free]*.
1. Aplique o código do cupom *35off*, ele atualizará o subtotal e o tornará menor que $75.
1. Verifique [!UICONTROL Order Summary] na etapa de pagamento.

<u>Resultados esperados</u>:

A seguinte mensagem é exibida: *O método de envio selecionado não está disponível. Selecione outro método de envio para este pedido.*

<u>Resultados reais</u>:

O preço de envio exibe *Ainda não calculado*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
