---
title: "MDVA-30945: um erro fatal durante as operações de adição e atualização do carrinho"
description: O patch MDVA-30945 corrige o problema em que você recebe um erro fatal *Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php* ao atualizar carrinhos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. O problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: erro fatal durante as operações de adição e atualização do carrinho

O patch MDVA-30945 corrige o problema em que você recebe um erro fatal *Chamada para uma função membro getValue() em nulo no produto-configurável-módulo CartItemProcessor.php* ao atualizar carrinhos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.7 está instalado. O problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um erro fatal de PHP depois que os produtos no carrinho são atualizados no Admin.

<u>Etapas a serem reproduzidas</u>:

1. No Commerce Admin, crie um produto configurável sem opções.
1. Adicione-o ao carrinho na loja.
1. Retorne ao Administrador, adicione opções configuráveis ao produto e salve as alterações.
1. Atualize a página do carrinho na loja.

<u>Resultados esperados</u>:

Na página do carrinho, a seguinte mensagem de validação é exibida: *Alguns dos produtos abaixo não têm todas as opções necessárias*.

<u>Resultados reais</u>:

A página do carrinho está em branco. No PHP `error.log`, o seguinte erro será registrado: *Exceção não capturada &#39;Error&#39; com a mensagem &#39;Call to a member function getValue() on null&#39; em vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
