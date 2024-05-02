---
title: "MDVA-31295: Pontos de fidelidade em pedidos parciais"
description: O patch MDVA-31295 corrige o problema em que os pontos de premiação não são calculados corretamente quando um pedido parcial é concluído e os itens são tributados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: pontos de fidelidade em ordens parciais

O patch MDVA-31295 corrige o problema em que os pontos de premiação não são calculados corretamente quando um pedido parcial é concluído e os itens são tributados. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.8 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce no local 2.3.0

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As recompensas não são aplicadas às contas dos clientes quando a ordem está completa (parcialmente entregue) e os itens são tributados. Quando os itens não são tributados, os prêmios são adicionados às contas dos clientes com sucesso.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon na loja como cliente.
1. Adicione dois produtos ao carrinho.
1. Vá para o checkout, defina o endereço de entrega que tem o imposto e faça o pedido.
1. No admin, vá para o pedido feito recentemente.
1. Clique em **Fatura** e defina **Qtde. para Fatura** a 0 para um dos itens e clique em **Atualizar quantidade**. Enviar fatura.
1. Clique em Entregar e defina **Quantidade a Ser Entregue** para 0 no item que não foi faturado. Clique em **Enviar Remessa**.
1. Clique em Cancelar pedido. O status será definido como Concluído.
1. No admin, acesse **Clientes** > Escolha a compra feita pelo cliente antes > **Pontos de recompensa** > **Histórico de pontos de premiação**.
1. Verifique os pontos de premiação ganhos do pedido feito.

<u>Resultados esperados</u>:

Os pontos de premiação devem ser calculados para pedidos tributáveis quando um pedido parcial é concluído.

<u>Resultados reais</u>:

Os pontos de recompensa não são calculados para uma ordem tributável quando uma ordem parcial é concluída.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
