---
title: "MDVA-39923: a pesquisa por SKU na funcionalidade de ordem rápida B2B diferencia maiúsculas de minúsculas"
description: O patch MDVA-39923 corrige o problema em que os clientes recebem um erro ao pesquisar o pedido por SKU na funcionalidade de pedido rápido B2B com um caso diferente daquele com o qual o nome é salvo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-39923. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: A pesquisa por SKU na funcionalidade de ordem rápida B2B diferencia maiúsculas de minúsculas

O patch MDVA-39923 corrige o problema em que os clientes recebem um erro ao pesquisar o pedido por SKU na funcionalidade de pedido rápido B2B com um caso diferente daquele com o qual o nome é salvo. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.2 está instalado. A ID do patch é MDVA-39923. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A pesquisa por SKU na funcionalidade de ordem rápida B2B diferencia maiúsculas de minúsculas e mostra um erro quando uma caixa diferente é usada daquela com a qual o SKU é salvo.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador e acesse **Lojas** > **Configuração** > **B2B**.
1. Ativar **Catálogo compartilhado** e **Pedido rápido**.
1. Crie um produto com SKU em maiúsculas, por exemplo, TEST20-1234
1. Atribuir o produto criado à **Catálogo compartilhado**.
1. Faça logon como cliente e clique em **Pedido rápido**.
1. Insira o SKU em minúsculas, por exemplo, test20-1234.

<u>Resultados esperados</u>:

O produto deve ser encontrado independentemente da caixa usada.

<u>Resultados reais</u>:

A seguinte mensagem de erro é recebida: *1 produto(s) requer(em) a sua atenção*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
