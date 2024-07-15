---
title: "MDVA-40101: os itens permanecem minicarrinho após o posicionamento do pedido Check-out do PayPal Express"
description: O patch MDVA-40101 corrige o problema em que os itens não são removidos do minicarrinho após um pedido bem-sucedido feito usando a Finalização de compra do PayPal Express. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 está instalada. A ID do patch é MDVA-40101. Observe que o problema foi corrigido no Adobe Commerce 2.4.0.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: os itens permanecem minicarrinho após o posicionamento do pedido Check-out do PayPal Express

O patch MDVA-40101 corrige o problema em que os itens não são removidos do minicarrinho após um pedido bem-sucedido feito usando a Finalização de compra do PayPal Express. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 está instalada. A ID do patch é MDVA-40101. Observe que o problema foi corrigido no Adobe Commerce 2.4.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.7

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os itens permanecem no minicarrinho mesmo após um pedido bem-sucedido feito usando a Finalização expressa do PayPal.

<u>Etapas a serem reproduzidas</u>:

Faça um pedido usando o PayPal Express Checkout no modo Incógnito em um navegador.

<u>Resultados esperados</u>:

O minicarrinho deve estar vazio após a conclusão bem-sucedida do pedido.

<u>Resultados reais</u>:

* A página de sucesso mostra um minicarrinho vazio.
* Todas as outras páginas mostram o minicarrinho com itens comprados.
* Clicar no link do carrinho o redireciona para uma página de carrinho vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
