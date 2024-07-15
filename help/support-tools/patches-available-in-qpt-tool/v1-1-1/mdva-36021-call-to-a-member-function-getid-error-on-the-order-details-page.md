---
title: "MDVA-36021: Os usuários recebem uma mensagem de erro ao abrir detalhes do pedido"
description: O patch MDVA-36021 resolve o problema em que os usuários recebem a mensagem de erro *Chamada para uma função de membro getId()* ao tentar abrir detalhes do pedido. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalada. A ID do patch é MDVA-36021. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021: Os usuários recebem uma mensagem de erro ao abrir detalhes do pedido

O patch MDVA-36021 resolve o problema em que os usuários recebem a mensagem de erro *Chamada para uma função de membro getId()* ao tentar abrir os detalhes do pedido. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalada. A ID do patch é MDVA-36021. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.1, 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando os usuários tentam abrir os detalhes do pedido, a seguinte mensagem de erro é exibida na página de detalhes do pedido no Admin: *report.CRITICAL: Erro: Chamada para uma função de membro getId() na matriz em /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

<u>Pré-requisitos</u>:

O sistema deve ter configurações de imposto e pedidos com alíquotas de imposto específicas.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce.
1. Vá para **Vendas** > **Pedidos** > **Pedido Aberto**.

<u>Resultados esperados</u>:

O pedido é aberto sem erros.

<u>Resultados reais</u>:

Você recebe uma mensagem de erro semelhante à seguinte: *report.CRITICAL: Erro: Chamada para uma função de membro getId() na matriz em /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
