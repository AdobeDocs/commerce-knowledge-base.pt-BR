---
title: "MDVA-35356: retorno de crédito de loja incorreto após cancelar a ordem parcialmente faturada"
description: O patch MDVA-35356 corrige o problema de retorno de crédito da loja incorreto após o cancelamento do pedido parcialmente faturado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35356. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356: retorno de crédito de armazenamento incorreto após cancelar pedido parcialmente faturado

O patch MDVA-35356 corrige o problema de retorno de crédito da loja incorreto após o cancelamento do pedido parcialmente faturado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.19 está instalado. A ID do patch é MDVA-35356. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie três produtos simples.
1. Crie um novo usuário e atribua o crédito da loja (Exemplo: crédito da loja = *$10,* preços simples do produto = *$ 100*, *$ 200*, e *$ 300*).
1. Faça logon com o usuário acima e adicione os três produtos ao carrinho.
1. Confira os três produtos no carrinho e utilize o crédito da loja para uma parte do pedido (Exemplo: pago com **Cheque/Ordem de pagamento**).
1. Execute duas faturas no pedido por meio da API, uma para o Produto 1 e outra para o Produto 2:

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. Observe que o crédito da loja é totalmente aplicado à primeira fatura.
1. &#x200B;Observe que o saldo de crédito da loja = *0*.
1. Cancele o pedido e veja se dois itens estão faturados e se o terceiro item foi cancelado.
1. Observe o saldo de crédito da loja.

<u>Resultados esperados</u>:

O saldo de crédito de armazenamento ainda é 0 porque o crédito de armazenamento de US$ 10 foi faturado.

<u>Resultados reais</u>:

O crédito total da loja é retornado: o saldo é de US$ 10.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
