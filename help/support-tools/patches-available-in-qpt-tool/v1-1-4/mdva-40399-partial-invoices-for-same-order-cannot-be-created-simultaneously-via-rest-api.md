---
title: 'MDVA-40399: faturas parciais para o mesmo pedido não podem ser criadas simultaneamente via API'
description: O patch MDVA-40399 corrige o problema em que faturas parciais para o mesmo pedido não podem ser criadas simultaneamente por meio da API Rest. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 está instalada. A ID do patch é MDVA-40399. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: faturas parciais para o mesmo pedido não podem ser criadas simultaneamente via API

O patch MDVA-40399 corrige o problema em que faturas parciais para o mesmo pedido não podem ser criadas simultaneamente por meio da API Rest. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 está instalada. A ID do patch é MDVA-40399. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Faturas parciais para os mesmos pedidos não podem ser criadas simultaneamente usando a API Rest.

<u>Pré-requisitos</u>:

Um produto configurável com pelo menos duas variações.

<u>Etapas a serem reproduzidas</u>:

1. Adicione ambas as variantes do produto configurável ao carrinho.
1. Coloque o pedido.
1. Crie duas faturas simultaneamente para o pedido por meio da API Rest.

<u>Resultados esperados</u>:

* Ambas as faturas devem ser criadas com sucesso.
* `qty_invoiced` deve ser atualizado para ambas as faturas na tabela `sales_order_item`.
* Ambos os produtos devem ter uma quantidade faturada.

<u>Resultados reais</u>:

* Ambas as NFFs são criadas com sucesso.
* `qty_invoiced` não é atualizado em relação a uma das faturas na tabela `sales_order_item`.
* Na página **Visualização do pedido** do Administrador, a quantidade de faturas é exibida somente para um produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
