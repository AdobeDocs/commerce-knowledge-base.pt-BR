---
title: "MDVA-34665: produtos de pacote desaparecem da página de categoria da loja"
description: O patch MDVA-34665 corrige o problema de produtos empacotados ausentes nas páginas de categoria. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-34665. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: produtos de pacote desaparecem da página de categoria da loja

O patch MDVA-34665 corrige o problema de produtos empacotados ausentes nas páginas de categoria. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-34665. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.4-2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

**Caso 1:**

<u>Pré-requisitos</u>:

1. Crie 15.000 produtos agrupados com um produto simples como uma opção de pacote. Não use o mesmo produto simples com vários produtos agrupados.
1. Produtos simples devem ser definidos como *Não visíveis individualmente*.

<u>Etapas a serem reproduzidas</u>:

1. Atribua 15 mil produtos agrupados em duas categorias, 7.500 cada.
1. Selecione todos os produtos simples (15k) e atualize o estoque usando as atualizações de atributo de massa do produto. Nosso objetivo é ter muitas IDs na tabela cl de pesquisa (as tabelas cl são as tabelas usadas pelo indexador para saber quais registros precisam ser atualizados).
1. Verifique se você tem 15K IDs na tabela `catalogsearch_fulltext_cl`.
1. Verifique se o indexador `indexer_update_all_views` foi executado.
1. Consulte a página de categoria continuamente e observe a contagem de produtos.

<u>Resultados esperados</u>:

A contagem de produtos deve permanecer como estava após a reindexação.

<u>Resultados reais</u>:

A contagem de produtos cai para 7.450 depois de algum tempo. Ele permanece em 7.450 mesmo após a conclusão da indexação.

**Caso 2:**

<u>Etapas a serem reproduzidas</u>:

1. Crie um pacote de produtos com um produto simples associado como uma opção.
1. Altere os modos do indexador para *atualizar na agenda*.
1. Atribua o produto do pacote a uma categoria.
1. Alterar o status do estoque do produto simples para *sem estoque*.
1. Execute cron; o produto do pacote desaparece da loja.
1. Adicione estoque de volta ao produto simples e salve.
1. Execute o indexador cron.
1. Atualize a página de categoria.

<u>Resultados esperados</u>:

O produto ainda está ausente.

<u>Resultados reais</u>:

O produto do pacote reaparece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
