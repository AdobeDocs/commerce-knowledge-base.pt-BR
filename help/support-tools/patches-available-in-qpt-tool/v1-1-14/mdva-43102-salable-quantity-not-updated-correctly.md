---
title: "MDVA-43102: Quantidade disponível não atualizada corretamente"
description: O patch MDVA-43102 corrige o problema em que a quantidade comercializável não é atualizada corretamente quando um reembolso é feito por meio da API REST. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-43102. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: Quantidade disponível não atualizada corretamente

O patch MDVA-43102 corrige o problema em que a quantidade comercializável não é atualizada corretamente quando um reembolso é feito por meio da API REST. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-43102. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade disponível não é atualizada corretamente quando um reembolso é feito usando a API REST.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um item ao carrinho.
1. Verifique a Qtd. em Estoque e a Qtd. Venável.
1. Criar um pedido.
1. Crie uma fatura, se necessário.
1. Submeta uma solicitação REST para reembolsar a NFF usando a seguinte carga útil:

   * método/ordem/`<order_id>`/reembolso offline
   * método online/fatura/`<invoice_id>`/reembolso

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Não entregar os itens.
1. Comparar a Quantidade em Estoque e a Quantidade Vendível de antes. Ambos devem ser atualizados pelo mesmo valor.

<u>Resultados esperados</u>:

A quantidade disponível é atualizada corretamente quando uma restituição é emitida antes do envio do pedido e o produto é devolvido ao estoque.

<u>Resultados reais</u>:

A quantidade disponível não é atualizada quando uma restituição é emitida antes do envio do pedido e o produto é devolvido ao estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
