---
title: "MDVA-38626: o usuário administrador não pode fazer pedidos usando o PayPal Payflow Pro"
description: O patch MDVA-38626 resolve o problema em que o usuário administrador não consegue fazer um pedido no back-end usando o método de pagamento PayPal Payflow Pro. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-38626. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: b9257d42-d8df-4dd6-b2b4-70ddd6f3e414
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-38626: O usuário administrador não pode fazer pedidos usando o PayPal Payflow Pro

O patch MDVA-38626 resolve o problema em que o usuário administrador não consegue fazer um pedido no back-end usando o método de pagamento PayPal Payflow Pro. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.9 está instalado. A ID do patch é MDVA-38626. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode fazer pedidos no backend usando o método de pagamento PayPal Payflow Pro.

<u>Etapas a serem reproduzidas</u>:

1. Configure o método de pagamento PayPal Payflow Pro.
1. Ir para **Clientes** > **Todos os Clientes** e criar uma conta de cliente.
1. Clique em **Criar pedido**.
1. Adicione qualquer item ao carrinho.
1. Tente fazer o pedido usando Payflow Pro.

<u>Resultados esperados</u>:

O pedido é feito.

<u>Resultados reais</u>:

O usuário recebe um erro 500. O log do relatório contém:

```
{"0":"No such entity with cartId = 0","1":"#1 Magento\\Quote\\Model\\QuoteRepository->loadQuote() called at [app\/code\/Magento\/Quote\/Model\/QuoteRepository.php:136]\n#2 Magento\\Quote\\Model\\QuoteRepository->get() called at [lib\/internal\/Magento\/Framework\/Interception\/Interceptor.php:58]\n#3 Mag
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
