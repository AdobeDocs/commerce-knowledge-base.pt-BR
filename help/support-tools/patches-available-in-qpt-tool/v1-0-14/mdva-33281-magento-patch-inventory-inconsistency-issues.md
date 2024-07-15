---
title: "Patch MDVA-33281: problemas de inconsistência do inventário"
description: O patch MDVA-33281 corrige três problemas de inconsistência de inventário. Clique nos problemas vinculados na seção Problema para ver as etapas para reproduzir esses erros. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 está instalada.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Correção do MDVA-33281: problemas de inconsistência do inventário

O patch MDVA-33281 corrige três problemas de inconsistência de inventário. Clique nos problemas vinculados na seção Problema para ver as etapas para reproduzir esses erros. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch corrige problemas de inconsistência do inventário como:

* **Erro fatal de PHP** ao executar `bin/magento inventory:reservation:list-inconsistencies` na CLI devido ao tipo incorreto de parâmetro SKU.
* **Dados duplicados** na lista de inconsistências.
* **Nova reserva** será criada antes do pedido ser feito (realização anterior com base na reserva após o pedido feito). Em caso de erros no posicionamento do pedido, uma reserva adicional será adicionada para compensar.

>[!NOTE]
>
>Também há um patch MDVA-30112 que resolve o problema em que há um número inesperadamente grande de [inconsistências de reserva](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) em nossa documentação do desenvolvedor, na tabela `inventory_reservation`. Para obter a solução, consulte o [patch de Magento MDVA-30112: grande número de inconsistências de reserva](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) em nossa base de dados de conhecimento de suporte.

## Erro fatal do PHP

<u>Etapas a serem reproduzidas</u>:

Erro fatal de PHP ao executar `bin/magento inventory:reservation:list-inconsistencies`.

Para obter uma lista de inconsistências de reserva, faça logon no servidor de produção e execute o seguinte comando na CLI (switch -r - saída bruta):

<pre>inventário bin/magento:reservation:list-inconsistencies -r</pre>

<u>Resultados esperados</u>:

A lista de inconsistências de reserva é criada. Eles serão retornados no seguinte formato

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Resultados reais</u>:

O erro fatal do PHP foi gerado.

## Dados duplicados

Os dados duplicados estão no `inventory_reservation table`.

<u>Etapas a serem reproduzidas</u>:

Para solucionar problemas de inconsistência de reserva, execute o seguinte comando:

<pre>SELECT *, COUNT(*)
DE_reserva_de_inventário
Metadados, sku, quantidade de GROUP BY
COM CONTAGEM(*) &gt; 1</pre>

<u>Resultados esperados</u>:

Nenhuma duplicação.

<u>Resultados reais</u>:

Há duplicatas.

## Nova reserva

<u>Etapas a serem reproduzidas</u>:

Nova reserva criada antes do pedido ser feito:

1. Importe o banco de dados.
1. Executar `bin/magento setup:upgrade` no terminal.
1. Listar inconsistências executando `bin/magento inventory:reservation:list-inconsistencies        -i -r` no terminal.

<u>Resultados esperados</u>:

Sem loop e resultados muito mais rápidos.

<u>Resultados reais</u>:

Os mesmos resultados são exibidos em um loop infinito ou o comando falha com `memory_limit`, dependendo das configurações do sistema.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
