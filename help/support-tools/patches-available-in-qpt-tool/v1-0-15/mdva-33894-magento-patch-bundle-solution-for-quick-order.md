---
title: '‘Correção MDVA-33894: solução de pacote para pedido rápido’'
description: O patch MDVA-33894 corrige vários problemas da funcionalidade de Pedido rápido, incluindo a adição e remoção de vários produtos e a diferenciação entre maiúsculas e minúsculas de SKU. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Correção MDVA-33894: solução de pacote para pedido rápido

O patch MDVA-33894 corrige vários problemas da funcionalidade de Pedido rápido, incluindo a adição e remoção de vários produtos e a diferenciação entre maiúsculas e minúsculas de SKU. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem e Adobe Commerce no local 2.4.0-2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch MDVA-33894 é uma solução de pacote com correções para os seguintes problemas:

* A funcionalidade **Minha Conta** > **Pedir por SKU** diferencia maiúsculas de minúsculas: se você inserir uma SKU válida, mas as maiúsculas e minúsculas não estiverem corretas (maiúsculas em vez de minúsculas e assim por diante), a Adobe Commerce emitirá um erro.
* Quando um comprador usa o Quick Order para adicionar vários produtos ao carrinho e tenta remover um produto, o produto não é removido.
* Problemas de diferenciação entre maiúsculas e minúsculas ao adicionar várias SKUs a um pedido em massa.
* Problema no cache da página de pedido rápido com SKUs inseridas anteriormente.
* A quantidade de pedidos rápidos não é refletida no carrinho.
* A duplicação de SKU não é validada corretamente.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
