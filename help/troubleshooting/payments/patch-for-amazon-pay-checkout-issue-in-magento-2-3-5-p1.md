---
title: Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1
description: Esta correção soluciona o problema de incapacidade de alterar um método de pagamento na etapa "Revisão e pagamentos" do check-out do widget de pagamentos, ao fazer check-out com o Amazon Pay no Adobe Commerce.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1

Esta correção soluciona o problema de incapacidade de alterar um método de pagamento na etapa &quot;Revisão e pagamentos&quot; do check-out do widget de pagamentos, ao fazer check-out com o Amazon Pay no Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem versão 2.3.5-p1
* Adobe Commerce no local versão 2.3.5-p1

## Problema

Quando um comprador finaliza a compra com o Amazon Pay, faz logon, prossegue para a etapa de pagamento e tenta alterar seu cartão de crédito de pagamento no widget de pagamentos, uma mensagem de erro é exibida. O check-out não pode ser concluído se o comprador ignorar o erro e prosseguir para o check-out.

Para resolver esse problema e remover o erro, criamos uma [correção](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip).

<u>Etapas a serem reproduzidas</u>:

1. Inicie o checkout com o Amazon Pay.
1. Faça logon como cliente do Amazon Pay.
1. Selecione o método de envio e prossiga para a etapa de pagamento.
1. Tente alterar o cartão de crédito para outro.

<u>Resultado esperado</u>: um cartão de crédito diferente é selecionado como método de pagamento sem um erro.

<u>Resultado real</u>: A mensagem de erro é exibida: *&quot;Entre em contato com este comerciante para obter ajuda para concluir seu pedido.&quot;*

## Solução

[Aplicar o patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) abaixo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar BUNDLE-2554\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem versão 2.3.5-p1
* Adobe Commerce no local versão 2.3.5-p1

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem versão 2.3.5
* Adobe Commerce no local versão 2.3.5

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na nossa base de conhecimento de suporte para obter instruções.

## Arquivos Anexados
