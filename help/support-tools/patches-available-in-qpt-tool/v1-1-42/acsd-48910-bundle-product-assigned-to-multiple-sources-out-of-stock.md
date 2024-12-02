---
title: 'ACSD-48910: o produto empacotado atribuído a várias fontes sai do estoque após a fatura e o envio'
description: Aplique o patch ACSD-48910 para corrigir o problema do Adobe Commerce em que o produto empacotado atribuído a várias fontes fica esgotado depois que um pedido é faturado e enviado, mesmo que ainda tenha uma quantidade diferente de zero.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: o produto empacotado atribuído a várias fontes sai do estoque após a fatura e o envio

O patch ACSD-48910 corrige o problema em que o produto empacotado atribuído a várias fontes sai do estoque depois que um pedido é faturado e enviado, mesmo que ainda tenha uma quantidade diferente de zero. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. A ID do patch é ACSD-48910. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto agrupado atribuído a várias fontes sai do estoque após o faturamento e o envio, mesmo que ainda esteja disponível.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites.
1. Criar duas lojas/visualizações de loja (uma por site).
1. Crie dois produtos simples (quantidade = 10) e atribua-os a estoques e sites.
1. Crie um produto agrupado e adicione esses produtos simples a ele. Atribua o produto incluído a ambos os sites.
1. Acesse a loja e adicione o produto incluído ao carrinho.
1. Confira e faça o pedido.
1. No Administrador, fature e envie o pedido.

<u>Resultados esperados</u>:

O produto incluso permanece no estoque, pois compramos apenas 1 dos 10 itens.

<u>Resultados reais</u>:

O produto incluído altera seu status para indisponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
