---
title: "MDVA-37068: imposto incorreto exibido na Finalização da compra de produtos virtuais"
description: O patch MDVA-37068 corrige o problema quando a Página de finalização exibe uma alíquota de imposto incorreta para produtos virtuais. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalada. A ID do patch é MDVA-37068. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: Imposto incorreto exibido na Finalização da compra de produtos virtuais

O patch MDVA-37068 corrige o problema quando a Página de finalização exibe uma alíquota de imposto incorreta para produtos virtuais. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalada. A ID do patch é MDVA-37068. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce (todos os métodos de implantação) 2.3.1-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A alíquota de imposto incorreta é exibida na Página de Finalização da compra quando o carrinho de compras tem apenas produtos virtuais.

<u>Pré-requisitos</u>:

1. Crie duas alíquotas e regras de imposto separadas para dois países diferentes - por exemplo, 10% e 1%.
1. Crie um produto virtual.
1. Executar reindexação e limpar cache.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente.
1. Adicione diferentes endereços de faturamento e de envio.
1. Adicione um produto virtual ao carrinho.
1. Verifique o carrinho e a página de check-out.

<u>Resultados esperados</u>:

O imposto exibido no carrinho e na página de check-out é o mesmo.

<u>Resultados reais</u>:

O imposto exibido no carrinho e na página de finalização da compra NÃO são os mesmos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
