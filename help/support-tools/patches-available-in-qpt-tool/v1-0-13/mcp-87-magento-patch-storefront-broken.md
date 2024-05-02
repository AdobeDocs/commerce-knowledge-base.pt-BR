---
title: "Patch do Adobe Commerce MCP-87: loja quebrada"
description: O patch do Adobe Commerce MCP-87 corrigiu o problema em que a reindexação de estoque de catálogos é lenta. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada.
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Correção do Adobe Commerce MCP-87: vitrine quebrada

O patch do Adobe Commerce MCP-87 corrigiu o problema em que a reindexação de estoque de catálogos é lenta. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.13 está instalado.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.0.

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação de estoque de catálogos com perfis grandes é muito lenta.

<u>Etapas a serem reproduzidas:</u>

1. Faça logon no Painel de administração.
1. Navegue até: **Produtos** > **Catálogo**.
1. Selecione todos os itens na grade Produtos.
1. Selecionar **Atualizar atributos** na lista suspensa Selecionar ações do produto. Clique em **Enviar**.
1. Clique em **Inventário avançado** na guia Configurações avançadas. Alterar **Disponibilidade do Stock** para *Em estoque*. Clique em **Salvar**.
1. Execute a reindexação completa manualmente e execute o seguinte comando a partir da raiz: `bin/magento indexer:reindex`

<u>Resultado esperado:</u>

O indexador de ações reindexa rapidamente.

<u>Resultado real:</u>

O indexador do Stock está muito lento e/ou não termina.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
