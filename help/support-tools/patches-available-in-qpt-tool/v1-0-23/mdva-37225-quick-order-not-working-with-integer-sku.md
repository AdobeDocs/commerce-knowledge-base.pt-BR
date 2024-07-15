---
title: "MDVA-37225: A ordem rápida não funciona com SKU de número inteiro"
description: O patch de qualidade MDVA-37225 para Adobe Commerce corrige o problema que ocorria quando a página não carregava ao criar uma ordem rápida quando havia um valor inteiro nos SKUs importados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalada. A ID do patch é MDVA-37225. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: A ordem rápida não funciona com SKU de número inteiro

O patch de qualidade MDVA-37225 para Adobe Commerce corrige o problema que ocorria quando a página não carregava ao criar uma ordem rápida quando havia um valor inteiro nos SKUs importados. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalada. A ID do patch é MDVA-37225. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.4.1-p1
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.4.1-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito</u>:

Adobe Commerce com módulo B2B instalado

<u>Etapas a serem reproduzidas</u>:

1. Habilitar a funcionalidade de ordem rápida B2B.
1. Crie 4 produtos simples com SKUs (Exemplo de SKUs: *00100*, *001E002*, *001E02C* e *7100824*).
1. Vá para a página ``<storefront_url>/quickorder`` no front-end e tente criar um pedido usando um arquivo CSV com este conteúdo de Exemplo:

| sku | qtd |
|---|---|
| 00100 | 1 |


<u>Resultados esperados</u>:

O produto (Exemplo: produto com SKU = *00100*) é adicionado ao carrinho, conforme esperado.

<u>Resultados reais</u>:

A página não é carregada e nenhum produto é adicionado ao carrinho.


## Aplicar o patch

Para aplicar patches individuais, use os seguintes links na documentação do desenvolvedor, dependendo do seu produto Adobe Commerce:

* Adobe Commerce e Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Leitura relacionada

Para saber mais sobre a Ferramenta de correções de qualidade em nossa base de conhecimento de suporte, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) em nossa base de dados de conhecimento de suporte.
