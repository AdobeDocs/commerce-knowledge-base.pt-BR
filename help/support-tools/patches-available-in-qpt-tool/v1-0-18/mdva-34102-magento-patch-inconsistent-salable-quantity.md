---
title: "MDVA-34102: quantidade vendável inconsistente"
description: O patch MDVA-34102 resolve o problema em que a quantidade de estoque padrão é zero para produtos desativados nas páginas Grade de produtos e Editar produto no Administrador. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é MDVA-34102. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: quantidade vendável inconsistente

O patch MDVA-34102 resolve o problema em que a quantidade de estoque padrão é zero para produtos desativados nas páginas Grade de produtos e Editar produto no Administrador. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.18 está instalado. A ID do patch é MDVA-34102. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Configure dois sites com lojas e visualizações de loja.
1. Criar uma fonte e um estoque adicionais.
1. Adicione um produto simples:
   * Definir **Ativar produto** = *Não*.
   * Atribuir duas fontes com **Status do item de origem** = *Em estoque* com uma quantidade maior que zero (Exemplo: **estoque padrão** = *123* e **Ações do Reino Unido** = *123*).
1. Salve o produto.
1. Verifique a **Quantidade de Produtos Venáveis** guia.

<u>Resultados esperados</u>:

Tanto o estoque padrão quanto o estoque do Reino Unido = *123.*

A quantidade de estoque padrão é mostrada corretamente para produtos desabilitados nas páginas Grade de de Produtos e Editar Produtos no Administrador.

<u>Resultados reais</u>:

O estoque padrão = *0* e ações do Reino Unido = *123.*

A quantidade de estoque padrão é zero para produtos desabilitados nas páginas Grade de de Produtos e Editar Produtos no Administrador.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
