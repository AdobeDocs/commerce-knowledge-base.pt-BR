---
title: "Correção MDVA-32545: as faturas de pedidos não são enviadas automaticamente"
description: O patch MDVA-32545 corrige o problema em que os emails de fatura não enviam automaticamente ao cliente pedidos feitos pelo administrador. Isso afeta qualquer método de pagamento com o tipo de transação **Venda**, como **Braintree** ou **Fluxo de pagamento do PayPal Pro**.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Correção MDVA-32545: as faturas de pedidos não são enviadas automaticamente

O patch MDVA-32545 corrige o problema em que os emails de fatura não enviam automaticamente ao cliente pedidos feitos pelo administrador. Isso afeta qualquer método de pagamento com o tipo de transação **Venda**, como **Braintree** ou **PayPal Payflow Pro**.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.2-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Habilite qualquer método de pagamento com o tipo de transação **Venda**. (Por exemplo: **Braintree** ou **PayPal Payflow Pro**.)
1. Crie um produto simples.
1. Crie uma conta de cliente no front-end.
1. Faça um pedido do administrador.

<u>Resultados esperados</u>:

O email da fatura é enviado ao cliente automaticamente, conforme esperado.

<u>Resultados reais</u>:

O email da fatura não é enviado ao cliente automaticamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
