---
title: "MDVA-31150: fatura sem informações de crédito de armazenamento"
description: O patch MDVA-31150 corrige o problema em que uma fatura é criada sem informações de crédito de armazenamento. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 está instalada. Observe que o problema será corrigido no Adobe Commerce versão 2.4.2.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: fatura sem informações de crédito de loja

O patch MDVA-31150 corrige o problema em que uma fatura é criada sem informações de crédito de armazenamento. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O v.1.0.8 está instalado. Observe que o problema será corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

* Este patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.5-p2.
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.0 a 2.3.5-p2 e 2.4.0 a 2.4.0-p1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Depois do pedido de fatura por API, as informações de saldo do cliente e cartão-presente usados não estão presentes na fatura.

<u>Etapas a serem reproduzidas</u>

1. Adicionar um valor de crédito da loja a uma conta de cliente: na barra lateral Admin, vá para **Clientes** > **Todos os clientes.**
1. Encontre o registro do cliente e clique em **Editar** na coluna Ação, depois **Crédito da loja** > Atualizar o saldo > **Salvar Cliente**.
1. Ir para a Loja e adicionar produtos ao carrinho.
1. Faça um pedido aplicando a quantia de cartão-presente ou crédito da loja como pagamento parcial.
1. Criar fatura usando `REST API>POST>/rest/V1/order/1/invoice` com carga útil:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. Obter a fatura recém-criada usando `REST API>GET>/rest/V1/invoices/1`.

<u>Resultado esperado</u>

O crédito da loja e o saldo do cartão-presente são retornados por Chamada de API.

<u>Resultado real</u>

O crédito da loja e o saldo do cartão-presente não são retornados pela Chamada de API.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
