---
title: "MDVA-31021: importação e exportação lentas se houver muitas opções de produtos"
description: O patch MDVA-31021 resolve o problema quando a Importação/Exportação demora mais do que o esperado com um grande número de opções de produto. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: importação e exportação lentas se houver muitas opções de produtos

O patch MDVA-31021 resolve o problema quando a Importação/Exportação demora mais do que o esperado com um grande número de opções de produto. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.7 está instalado.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Se houver 100 mil registros ou mais no `catalog_product_option` , a validação do arquivo da função Importar/Exportar demora mais do que o esperado. Antes de Importar/Exportar, para verificar a validação da opção, o Adobe Commerce carrega opções de produto para todos os produtos existentes.

<u>Pré-requisitos</u>:

Loja Adobe Commerce com 5.000 produtos com opções personalizadas. Cada produto deve ter pelo menos quatro opções personalizadas, com duas ou mais opções para escolher, de modo que haja 100.000 registros em `catalog_product_option` tabela.

<u>Etapas a serem reproduzidas</u>:

1. Para um **Importar** exemplo: crie um arquivo de importação de CSV com um dos SKUs do administrador do Commerce.
1. Adicione quatro opções personalizadas ao arquivo de importação de CSV.
1. Tente importar o arquivo CSV do Commerce Admin.

<u>Resultados esperados</u>:

A função Importar ou Exportar é concluída conforme esperado. A validação leva menos de 10 segundos para ser concluída com um produto.

<u>Resultados reais</u>:

A função Importar ou Exportar demora mais do que o esperado. A validação leva mais de 10 segundos para ser concluída com apenas um produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
