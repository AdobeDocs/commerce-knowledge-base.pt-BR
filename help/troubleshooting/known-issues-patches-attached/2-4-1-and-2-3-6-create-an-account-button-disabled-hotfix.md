---
title: Adobe Commerce 2.4.1 e 2.3.6 criam um hotfix de botão de conta desativado
description: Este artigo fornece uma correção para o problema quando você luta para criar uma nova conta depois de inserir um valor incorreto em qualquer campo do formulário. Por exemplo, ao inserir um endereço de email no formato errado, deixar os campos de nome ou sobrenome vazios ou não inserir um valor que atenda aos requisitos de senha. Uma correção permanente será incluída nas versões do primeiro trimestre (2.4.2, 2.4.1-p1 e 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 e 2.3.6 criam um hotfix de botão de conta desativado

Este artigo fornece uma correção para o problema quando você luta para criar uma nova conta depois de inserir um valor incorreto em qualquer campo do formulário. Por exemplo, ao inserir um endereço de email no formato errado, deixar os campos de nome ou sobrenome vazios ou não inserir um valor que atenda aos requisitos de senha. Uma correção permanente será incluída nas versões do primeiro trimestre (2.4.2, 2.4.1-p1 e 2.3.6-p1).

## Problema

A variável **Criar uma conta** botão no **Criar nova conta** A página permanecerá desativada se um comprador tiver inserido dados inválidos. Isso impede que os compradores tentem criar uma conta novamente após cometer um erro.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Criar nova conta de cliente**.
1. Preencha os campos do formulário. No **Senha** , valores de entrada que não atendem aos requisitos de senha. Por exemplo:
   * As senhas no **Senha** e a variável **Confirmar senha** os campos não correspondem.
   * As senhas no **Senha** e a variável **Confirmar senha** Os campos não são longos o suficiente.
1. Clique em **Criar uma conta** botão.

<u>Resultados esperados</u>:

* **Criar uma conta** O botão deve permanecer ativo/ativado.
* O usuário deve conseguir criar uma nova conta.

<u>Resultados reais</u>:

* **Criar uma conta** O botão permanece desativado mesmo após preencher todos os campos obrigatórios com dados válidos/corretos.
* O cliente não pode criar uma nova conta.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir: [Baixar MC-38509-composer.patch](assets/MC-38509-composer.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.3.6 e 2.4.1.
* Adobe Commerce no local 2.3.6 e 2.4.1.

O patch não é compatível com outras versões e edições do Adobe Commerce.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Leitura relacionada

* [GitHub Adobe Commerce > Enviar formulário inválido para criar conta deixa o botão enviar desativado](https://github.com/magento/magento2/issues/30513)
* [Guia do usuário do Adobe Commerce > Introdução > Criação de uma conta](https://docs.magento.com/user-guide/magento/magento-account-create.html)
