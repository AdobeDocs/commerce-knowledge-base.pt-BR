---
title: "MDVA-33453: a visualização do Page Builder interrompe o preço do produto em diferentes sites"
description: O patch MDVA-33453 resolve o problema em que a pré-visualização do Page Builder é interrompida se os produtos correspondentes tiverem um preço diferente para cada site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: O preço do produto das interrupções da visualização do Page Builder é diferente entre os sites

O patch MDVA-33453 resolve o problema em que a pré-visualização do Page Builder é interrompida se os produtos correspondentes tiverem um preço diferente para cada site. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.6 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A pré-visualização de produto do Page Builder é interrompida quando há um produto com preços diferentes em sites diferentes.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel de administração do Commerce.
1. Crie dois sites.
1. Crie um produto simples.
1. Defina um preço diferente para o produto em cada site.
1. Execute cron e reindexe.
1. Crie ou edite uma página do CMS e use o bloco de produtos para adicionar o produto.

<u>Resultado real</u>:<br>

O erro abaixo ocorre:

*Modelo de filtragem de erros: já existe um item (Magento\\Catalog\\Model\\Product\\Interceptor) com a mesma identificação &quot;2&quot;.*

<u>Resultado esperado</u>:<br>

Nenhum erro é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
