---
title: "MDVA-30815: Elasticsearch resultados de pesquisa em branco"
description: O patch MDVA-30815 corrige o problema em que o Elasticsearch exibe uma página em branco quando as opções de limitador dos resultados da pesquisa são alteradas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.5.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: resultados da pesquisa em branco de Elasticsearch

O patch MDVA-30815 corrige o problema em que o Elasticsearch exibe uma página em branco quando as opções de limitador dos resultados da pesquisa são alteradas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao usar o Elasticsearch, se você alterar as opções do limitador de resultados da pesquisa, o Adobe Commerce exibirá uma página em branco.

<u>Pré-requisitos</u>:

O Elasticsearch está **habilitado**. Vá para **LOJAS** > **Configurações** > **Configuração** > **Catálogo** > **Pesquisa de Catálogo**.

<u>Etapas a serem reproduzidas</u>:

1. Vá para o seu site.
1. Procure um produto no campo de pesquisa principal.
1. Depois que as páginas de resultados da pesquisa forem exibidas, clique em na última página nas páginas de resultados da pesquisa.
1. Selecione **Mostrar xx por página** na opção limitador. Verifique se esse é um limite de número de resultado de pesquisa diferente do configurado atualmente.

<u>Resultados esperados</u>:

A página exibe o número configurado de resultados do produto.

<u>Resultados reais</u>:

Uma página em branco é exibida. Este erro também pode ser visto no `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: erro de sintaxe ou violação de acesso: 1064 Você tem um erro na sintaxe SQL; verifique o manual que corresponde à versão do seu servidor MySQL para obter a sintaxe correta a ser usada próximo a&#39;\`*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
