---
title: "MDVA-30112: grande número de inconsistências de reserva"
description: O patch MDVA-30112 resolve o problema em que você tem um número inesperadamente grande de [inconsistências de reserva](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) na tabela "inventory_reservation". As inconsistências de reserva incluem pedidos em aberto não registrados e pedidos completos que não estão registrados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: inconsistências de reserva de grande número

O patch MDVA-30112 resolve o problema em que você tem um número inesperadamente grande de [inconsistências de reserva](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) no `inventory_reservation` tabela. As inconsistências de reserva incluem pedidos em aberto não registrados e pedidos completos que não estão registrados. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.8 está instalado. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável [tamanho de grupo](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) value é o valor de quantos pedidos devem ser carregados de uma só vez. Quando há mais pedidos que esse valor, a Adobe Commerce considera os pedidos com status pendente como inconsistências.

>[!NOTE]
>
>Há um patch MDVA-33281 que corrige três outros problemas de inconsistência do inventário. Isso inclui um erro fatal do PHP durante a execução `bin/magento inventory:reservation:list-inconsistencies` na CLI. Outro problema que é corrigido são os dados duplicados na lista de inconsistências. Além disso, o problema em que uma reserva é criada antes do pedido feito (realização anterior com base na reserva após o pedido feito). Para obter a solução, consulte [MDVA-33281: problemas de inconsistência do inventário](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) em nossa base de conhecimento de suporte.

<u>Pré-requisitos</u>:

Execute o seguinte comando na CLI para listar as inconsistências de reserva no `inventory_reservation` tabela:

```
magento inventory:reservation:list-inconsistencies
```

Você vê um número inesperadamente grande de inconsistências de reserva e/ou o comando nunca é concluído.

<u>Etapas a serem reproduzidas</u>:

1. Execute o seguinte comando na CLI para resolver as inconsistências:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Faça três pedidos:
   * Atribua um único produto a cada um.
   * Use o método de pagamento Cheque/Ordem de pagamento para que o status do pedido seja &quot;pendente&quot;.
1. Você pode ver três registros com quantidade -1 na `inventory_reservation` tabela. Execute o seguinte comando na CLI para ver as inconsistências:

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Isso não retorna resultados, o que está correto.

1. Execute o seguinte comando na CLI:

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   Você vê que os pedidos de status &quot;pendentes&quot; são mostrados como inconsistências.

1. Execute o seguinte comando na CLI:

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>Resultados esperados</u>:

A Adobe Commerce não deve resolver inconsistências de pedidos de status &quot;pendentes&quot;. As inconsistências de estoque devem ser resolvidas para pedidos com status &quot;concluído&quot;, &quot;fechado&quot; e &quot;cancelado&quot;.

<u>Resultados reais</u>:

Quando há pedidos maiores que o valor de tamanho de grupo especificado, o Adobe Commerce considera pedidos com status &quot;pendente&quot; como inconsistências e adiciona vários registros de resolução de inconsistência para a mesma ordem.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
