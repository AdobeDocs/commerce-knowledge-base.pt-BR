---
title: "Patch MDVA-30284: Elasticsearch 7 - Limite do total de campos [XXXXX] no índice excedido"
description: O patch MDVA-30284 resolve o problema em que você recebe uma mensagem de erro de que "O limite do total de campos \[XXXXX\] no índice foi excedido" ao usar o Elasticsearch 7. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 está instalada. A ID do patch é MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Patch MDVA-30284: Elasticsearch 7 - Limite de campos totais [XXXXX] no índice foi excedido

O patch MDVA-30284 resolve o problema em que você recebe uma mensagem de erro de que &quot;O limite do total de campos \[XXXXX\] no índice foi excedido&quot; ao usar o Elasticsearch 7. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O v.1.0.5 está instalado. A ID do patch é MDVA-30284.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.5-p2
* O Elasticsearch 7 é compatível com o Adobe Commerce 2.3.5 e 2.4.x

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O limite de campos Elasticsearch está errado, resultando no seguinte erro ao executar o indexador \[catalogsearch\_fulltext\]:

*Limite do total de campos [xxx] no índice [xxxxxx] foi excedido*

Esse problema ocorre quando você tem um grande número de atributos de produto. O problema é acionado pela maneira como o Elasticsearch calcula a contagem de campos. Às vezes, quando houver atributos com campos atribuídos a eles, esses campos serão indexados como indexadores separados. Isso resulta no limite ter sido excedido no aviso.

<u>Etapas a serem reproduzidas:</u>

<u>Pré-requisitos</u>

* Módulo-elasticsearch 100.3.5 instalado.
* Elasticsearch 7 instalado.
* Configure o Elasticsearch como um back-end de pesquisa.

1. Crie mais de 1000 atributos para produtos.
1. Crie produtos para cada família.
1. Executar indexador.

<u>Resultado esperado:</u>

Todos os produtos estão disponíveis no índice Elasticsearch.

<u>Resultado real:</u>

1. Erro de Elasticsearch:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Novo produto não indexado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
