---
title: "MDVA-31282: autorização dupla no Paypal PayFlow Pro"
description: O patch MDVA-31282 resolve o problema quando ocorrem autorizações duplas no Paypal PayFlow Pro no Adobe Commerce. As autorizações duplas também têm o efeito de ignorar os filtros de fraude do PayFlow Pro e duplicar as taxas de transação. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: autorização dupla no Paypal PayFlow Pro

O patch MDVA-31282 resolve o problema quando ocorrem autorizações duplas no Paypal PayFlow Pro no Adobe Commerce. As autorizações duplas também têm o efeito de ignorar os filtros de fraude do PayFlow Pro e duplicar as taxas de transação. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.3.3 e 2.3.5 - 2.3.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As autorizações duplas ocorrem no PayPal PayFlow Pro no Adobe Commerce, que têm o efeito de ignorar os filtros de fraude do PayFlow Pro e duplicar as taxas de transação.

<u>Pré-requisitos</u>:

Configure o método de pagamento PayPal PayFlow Pro.

<u>Etapas a serem reproduzidas</u>:

1. Vá para o front-end como cliente convidado.
1. Adicionar produtos ao **Carrinho de Compras** a partir das páginas de produtos.
1. Vá para **Check-out**.
1. Especifique **Endereço de remessa** como um endereço em País \#1 (Exemplo: endereço do Reino Unido) e selecione um método de remessa.
1. Selecione **PayPal PayFlow Pro** como método de pagamento. Especifique o **Endereço de cobrança** como um endereço em País \#2 (Exemplo: endereço dos EUA).
1. Insira os dados do cartão de crédito e faça o pedido.
1. Navegue até **Vendas** > **Pedidos** em administração e observe a ordem criada.

<u>Resultados esperados</u>:

* O bloco de Informações de Pagamento exibe: *&quot;Filtros de Fraude Disparados: RESPMSG: Em revisão pelo Serviço de Fraude*. *A ordem está no status de Suspeita de Fraude&quot;*.
* O Paypal PayFlow Pro mostra uma única transação de autorização conforme esperado.

<u>Resultados reais</u>:

* O bloco de Informações de Pagamento exibe: *&quot;Filtros de Fraude Disparados: RESPMSG: Em revisão pelo Serviço de Fraude*. *A ordem está no status Processando&quot;*.
* Paypal PayFlow Pro mostra transações de autorização duplas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
