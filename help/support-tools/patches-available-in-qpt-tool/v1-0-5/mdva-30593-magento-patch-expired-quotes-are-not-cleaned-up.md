---
title: "Patch MDVA-30593: as aspas expiradas não são limpas'"
description: O patch MDVA-30593 resolve o problema em que as aspas expiradas de acordo com a configuração **Duração da cotação** não são excluídas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.4.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Correção MDVA-30593: as aspas expiradas não são excluídas

O patch MDVA-30593 resolve o problema em que as aspas expiradas de acordo com a configuração **Duração da Cotação** não são excluídas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.4.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.3.x

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As cotações que expiraram de acordo com a configuração **Tempo de vida da cotação** não são excluídas.

<u>Etapas a serem reproduzidas:</u>

1. No Administrador do Commerce, vá para **Lojas** > **Configuração** > **Vendas** > **Check-out** > **Carrinho de Compras**.
1. Definir **Duração da Cotação (dias)** = *1*
1. Salve a configuração e limpe o cache.
1. Faça logon como cliente.
1. Adicione um produto ao carrinho.
1. Depois de um dia, volte ao carrinho.

<u>Resultado esperado:</u>

A cotação é limpa e o produto é removido do carrinho, já que o preço antigo não é mais válido.

<u>Resultado real:</u>

O produto ainda está no carrinho.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
