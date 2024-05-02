---
title: "MDVA-37916: Pagamentos do PayPal Avançados não retornam à página de confirmação"
description: O patch de qualidade MDVA-37916 para Adobe Commerce corrige a questão de PayPal Payments Advanced não retornar à página de confirmação após o pagamento. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalada. A ID do patch é MDVA-37916. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: Pagamentos do PayPal Avançados não retornam à página de confirmação

O patch de qualidade MDVA-37916 para Adobe Commerce corrige a questão de PayPal Payments Advanced não retornar à página de confirmação após o pagamento. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.25 está instalado. A ID do patch é MDVA-37916. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.3.6-p1

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.6-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cliente não é levado para a página Confirmação de Pagamento após o pagamento ao usar o método Avançado de Pagamentos do PayPal.

<u>Etapas a serem reproduzidas</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Adicione o produto ao carrinho e navegue até a etapa de pagamento da página de finalização.
1. Selecionar **Cartão de Crédito (Fluxo de Pagamento Avançado)** opção de pagamento.
1. Clique em **Continuar** para exibir o iframe com o formulário de pagamento.
1. Preencha o formulário de pagamento com os detalhes do cartão de crédito da sandbox.
   * Número do cartão: 4444 333 222 1111 ou 4111 111 111 111 1111
   * Data de expiração: 23/12
   * CSC: 123
1. Clique em **Pagar agora**.

<u>Resultados esperados</u>:

Depois que o pagamento for processado e bem-sucedido, você será redirecionado para a página Confirmação do pedido.

<u>Resultados reais</u>:

* Você NÃO é redirecionado à página Confirmação do pedido.
* Mas o pedido foi criado no Adobe Commerce.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Leitura relacionada

Para saber mais sobre a Ferramenta de correções de qualidade em nossa base de conhecimento de suporte, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção em nossa base de conhecimento de suporte.
