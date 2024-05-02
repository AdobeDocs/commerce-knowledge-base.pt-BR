---
title: 'MDVA-37224: Não é possível pagar "cotação negociável" com PayFlow Pro'
description: O patch MDVA-37224 corrige o problema quando os clientes não conseguem pagar por uma **Cotação negociável** com o Paypal PayFlow Pro. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalada. A ID do patch é MDVA-37224. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: Não é possível pagar &quot;cotação negociável&quot; com o PayFlow Pro

O patch do MDVA-37224 corrige o problema quando os clientes não conseguem pagar por um **Cotação Negociável** com Paypal PayFlow Pro. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.23 está instalado. A ID do patch é MDVA-37224. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.6-p1
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.3-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisitos</u>:

* Adobe Commerce com módulo B2B instalado
* Funcionalidade da empresa habilitada
* **Cotação Negociável** funcionalidade ativada
* Existe um usuário da empresa
* O método de pagamento PayFlow Pro do PayPal está habilitado e configurado
* O método de pagamento PayFlow Pro do PayPal é permitido para B2B
* 2 produtos com preços diferentes foram criados

<u>Etapas a serem reproduzidas</u>:

1. Abra a Loja.
1. Adicionar **Product 1** ao carrinho de compras.
1. Criar um **Cotação Negociável** para **Product 1**.
1. Adicionar **Product 2** ao carrinho de compras.
1. No Administrador, aceite o **Cotação Negociável** criado na Etapa 3.
1. Na Loja, abra este **Cotação Negociável** e prossiga para o check-out.
1. Selecione o **Método de pagamento** = *PayPal PayFlow Pro* no **Revisão e Pagamentos** etapa.
1. Coloque o pedido.

<u>Resultados esperados</u>:

* O pedido foi feito com sucesso, conforme esperado.
* O PayPal envia um email com as informações corretas para o cliente, conforme esperado.

<u>Resultados reais</u>:

* A página da Web trava e não conclui o pedido.
* O PayPal envia uma confirmação para o cliente com valores zero, semelhante a este Exemplo:

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* 
   * [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
