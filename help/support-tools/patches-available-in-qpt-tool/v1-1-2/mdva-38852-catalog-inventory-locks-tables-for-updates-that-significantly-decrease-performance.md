---
title: "MDVA-38852: O inventário de catálogo bloqueia as tabelas, o que diminui o desempenho"
description: O patch MDVA-38852 resolve o problema em que o inventário de catálogo bloqueia as tabelas para atualizações, o que diminui significativamente o desempenho quando vários pedidos paralelos são feitos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-38852. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.
exl-id: 6ecee9c8-1f39-47de-8fbc-55e30cc936af
feature: Catalog Management, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-38852: O inventário de catálogo bloqueia as tabelas, o que diminui o desempenho

O patch MDVA-38852 resolve o problema em que o inventário de catálogo bloqueia as tabelas para atualizações, o que diminui significativamente o desempenho quando vários pedidos paralelos são feitos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.2 está instalado. A ID do patch é MDVA-38852. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O inventário de catálogo bloqueia as tabelas para atualizações, o que diminui significativamente o desempenho nos casos em que várias ordens paralelas são feitas.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um produto ao carrinho.
1. Prossiga para o check-out e tente fazer um pedido.

<u>Resultados esperados</u>:

* Não há impasses.
* O desempenho não é reduzido nos casos em que vários pedidos paralelos são feitos.

<u>Resultados reais</u>:

* Fazer um pedido é extremamente lento quando há vários usuários simultâneos.
* Ocorrem erros de deadlock com a seguinte aparência:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
