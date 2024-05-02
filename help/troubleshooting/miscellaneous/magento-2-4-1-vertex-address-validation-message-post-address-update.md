---
title: Atualização de postagem de endereço da mensagem de validação do Endereço Vertex do Adobe Commerce 2.4.1
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1 em que a validação do endereço Vertex não funciona durante a etapa de Pagamento quando é usado um endereço de entrega diferente do endereço de cobrança. O problema está programado para ser corrigido no Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Atualização de postagem de endereço da mensagem de validação do Endereço Vertex do Adobe Commerce 2.4.1

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1 em que a validação do endereço Vertex não funciona durante a etapa de Pagamento quando é usado um endereço de entrega diferente do endereço de cobrança. O problema está programado para ser corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.1 com integração Vertex habilitada
* Adobe Commerce na infraestrutura em nuvem 2.4.1 com integração Vertex ativada

## Problema

Pré-requisitos:

Ativar **Limpeza de endereço Vertex**. Para obter etapas, consulte [Configurando a limpeza do endereço da vitrine](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) em nosso guia do usuário.

<u>Etapas a serem reproduzidas:</u>

1. Crie uma conta e faça logon.
1. Adicione um item ao carrinho clicando em **Adicionar ao carrinho**. Clique no ícone Carrinho e clique em **Prosseguir para o check-out**.
1. Insira um endereço válido na caixa **Endereço de entrega** campo.
1. Marque uma das opções em **Métodos de envio**. Clique em **Próxima**.
1. Se a Validação de Endereço sugerir informações de endereço diferentes, clique em **Atualizar endereço** e clique em **Próxima**.
1. Desmarque a opção **Meus endereços de cobrança e de entrega são iguais** caixa de seleção

<u>Primeiro cenário:</u>

Siga as [acima de seis etapas](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) e depois:

1. Digite um novo endereço de cobrança válido.
1. Clique no link **Atualizar** botão. Ele mostrará a mensagem/sugestão da seguinte maneira: *Endereço inválido.* A seguir, uma sugestão de endereço como: *Código postal : XXXXX- XXXX Rua : XXX Rua da cidade XXX*
1. Clique no link **Atualizar** (não clique no botão **Atualizar endereço** botão da sugestão de endereço Vertex).
1. Clique no link **Editar** botão do endereço de cobrança atualizado.
1. Selecione o endereço na lista suspensa de endereços.
1. Clique no link **Atualizar** botão.

<u>Resultado esperado:</u>

A mensagem de validação/sugestão antiga é removida.

<u>Resultado real:</u>

A mensagem/sugestão de validação *&quot;Não encontramos um endereço válido Código postal: Rua XXXXX-XXXX : Rua XXX da cidade XXX&quot;* a mensagem é **NOT** removido. O mesmo problema ocorre se você inserir um endereço inválido no formulário.

<u>Segundo cenário:</u>

Siga as [acima de seis etapas](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) e depois:

1. Preencha o formulário de endereço com um endereço válido.
1. Clique no link **Atualizar** botão. Ele mostrará a mensagem/sugestão da seguinte maneira: *Endereço inválido.* A seguir, uma sugestão de endereço como: *Código postal : Rua XXXXX-XXXX : Rua XXX da cidade XXX*.
1. Clique no link **Atualizar** (não clique no botão **Atualizar endereço** botão de sugestão de endereço de vértice).
1. Verifique a ***Meus endereços de cobrança e de entrega são iguais*** menu suspenso.

<u>Resultado esperado:</u>

A mensagem de validação/sugestão antiga é removida.

<u>Resultado real:</u>

A mensagem/sugestão de validação *&quot;Não encontramos um endereço válido Código postal: Rua XXXXX-XXXX Rua XXX Rua XXX Cidade XXX&quot;* a mensagem é **NOT** removido. O mesmo problema ocorre se você inserir um endereço inválido no formulário.

## Leitura relacionada em nossa base de conhecimento de suporte:

[Problema conhecido do Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1: não é possível fazer logon no dotdigital quando a conta está ativada](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
