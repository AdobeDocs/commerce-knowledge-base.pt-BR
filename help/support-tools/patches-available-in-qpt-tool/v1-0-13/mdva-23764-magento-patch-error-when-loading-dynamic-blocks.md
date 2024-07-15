---
title: "Correção de Magento MDVA-23764: erro ao carregar blocos dinâmicos"
description: O patch MDVA-23764 Magento corrige o erro em
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Correção de Magento MDVA-23764: erro ao carregar blocos dinâmicos

O patch MDVA-23764 Magento corrige o erro em

```php
JsFooterPlugin.php
```

que afeta a exibição de blocos dinâmicos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalada. Observe que o problema foi corrigido na Magento 2.3.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Magento:** Magento Commerce Cloud 2.3.3.

**Compatível com as versões de Magento:** Magento Commerce e Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas:</u>

Tente carregar um URL que se pareça com o seguinte: https://\[magento domain\]/banner/ajax/load/.

<u>Resultado real:</u>

Um erro semelhante ao seguinte é lançado: *Uncaught TypeError: strpos() espera que o parâmetro 1 seja uma sequência de caracteres, nulo fornecido em...(linha de código)* .

<u>Resultado esperado:</u>

O URL é carregado sem erros.

## Aplicar o patch

Para obter instruções sobre como aplicar um patch QPT, use os seguintes links, dependendo do seu produto Magento:

* Magento Commerce: DevDocs [Aplique patches usando a Ferramenta de Patches de Qualidade](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Atualizações e Patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se o patch está disponível para o problema de Magento usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
