---
title: "MDVA-31006: Erro de pedidos 10415 duplicados do Paypal"
description: O patch MDVA-31006 corrige o problema em que o uso do pagamento de check-out do PayPal Express cria pedidos duplicados com um erro 10415. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. O problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: Erro de pedidos 10415 duplicados do Paypal

O patch MDVA-31006 corrige o problema em que o uso do pagamento de check-out do PayPal Express cria pedidos duplicados com um erro 10415. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. O problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.4.0

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário não está sendo enviado à página de sucesso do pedido do Adobe Commerce, portanto, atualiza a página em branco e o segundo pedido é feito, causando pedidos duplicados.

<u>Pré-requisitos</u>:

* Adobe Commerce instalado.
* O pagamento de finalização de compra do PayPal Express está configurado.
* Faça logon no administrador do Commerce. Vá para **Lojas** > **Configuração** > **Vendas** > **Métodos de Pagamento** > selecione **Check-out Expresso do Paypal** > **Configurar** > **Configurações Avançadas** > **Ignorar Etapa de Revisão do Pedido** > *Não*.

<u>Etapas a serem reproduzidas</u>:

1. Efetue logon como usuário.
1. Selecione um item e clique em **Adicionar ao carrinho**.
1. Clique no carrinho e clique em **Prosseguir para a finalização da compra**.
1. Vá para a janela do PayPal Express e faça um pagamento.
1. Você será redirecionado para a Página Revisão do Pedido Adobe Commerce.
1. Pressione o botão **Fazer pedido**.
1. Emular erro do sistema devido a problemas de infraestrutura do servidor. O usuário verá uma página em branco.
1. Atualize a página.

<u>Resultados esperados</u>:

* O cliente é redirecionado para a página Revisão do Pedido e vê a mensagem de erro &quot;*Uma transação de pagamento bem-sucedida já foi concluída. Verifique se o pedido foi feito.*&quot;
* No payment.log, localizado em `/var/log/payment.log`, há um erro 10415, mas apenas um pedido foi criado.

<u>Resultados reais</u>:

* Como o cliente não é enviado para a página de sucesso do pedido Adobe Commerce, ele atualiza a página em branco e um segundo pedido é feito, então dois pedidos duplicados são criados.
* No payment.log, localizado em `/var/log/payment.log`, há um erro 10415.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
