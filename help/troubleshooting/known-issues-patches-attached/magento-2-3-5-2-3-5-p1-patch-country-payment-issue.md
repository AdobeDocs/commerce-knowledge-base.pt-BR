---
title: "Correção 2.3.5, 2.3.5-p1 do Adobe Commerce: problema de pagamento do país"
description: Este patch soluciona um problema no Adobe Commerce em que o fluxo de trabalho de finalização da loja não exibia nenhum método de pagamento habilitado para países específicos, exceto para o Klarna e o Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Correção 2.3.5, 2.3.5-p1 do Adobe Commerce: problema de pagamento do país

Este patch soluciona um problema no Adobe Commerce em que o fluxo de trabalho de finalização da loja não exibia nenhum método de pagamento habilitado para países específicos, exceto para o Klarna e o Amazon Pay.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.5 e 2.3.5-p1
* Adobe Commerce no local 2.3.5 e 2.3.5-p1

## Problema

Quando uma loja tem o Amazon Pay e outro pagamento atribuído a diferentes países e quando um desses países e métodos de pagamento é selecionado, os botões método de pagamento e colocar ordem não ficam visíveis.

Uma atualização da página da Web é uma solução alternativa para o problema.

Para resolver esse problema e remover o erro, criamos uma [correção](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>Pré-requisitos</u>:

* Um produto simples é criado.
* **Cheque/Ordem de pagamento** é permitido somente para países específicos (em **Loja** > **Configuração** > **Vendas** > **Métodos de pagamento**).

* Exemplo: Pagamento dos Países Aplicáveis = Países Específicos
* Exemplo: pagamento de países específicos = Reino Unido

<u>Etapas a serem reproduzidas</u>:

1. Acesse a Loja como Convidado.
1. Adicione um produto simples ao carrinho de compras.
1. Vá para Check-out.
1. Preencha o formulário com dados válidos.

   * País = *Estados Unidos*

1. Selecione a taxa de envio e clique em **Próxima**.

   * A etapa de pagamento está aberta.
   * Não há pagamentos disponíveis.
   * Mensagem: **Nenhum método de pagamento disponível.**
   * Não há **Fazer pedido** botão.

1. Volte para o **Etapa de envio** e altere o valor para:

   * País = *Reino Unido*

1. Selecione a taxa de envio e clique em **Próxima**.

<u>Resultado esperado</u>:

A etapa de Pagamento é aberta.

* **Dinheiro Na Entrega** é exibida.
* **Cheque/Ordem de pagamento** é exibida.
* A variável **Fazer pedido** é exibido.

<u>Resultado real</u>:

A etapa de Pagamento é aberta.

* Não há pagamentos disponíveis.
* Mensagem: *Nenhum método de pagamento disponível.*
* Não há **Fazer pedido** botão.

## Solução

[Aplicar o patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) abaixo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar BUNDLE-2546\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.3.5 e 2.3.5-p1
* Adobe Commerce no local 2.3.5 e 2.3.5-p1

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce versões 2.3.4-p2 - 2.2.6

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na nossa base de conhecimento de suporte para obter instruções.

## Arquivos Anexados
