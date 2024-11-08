---
title: Adobe Commerce 2.4.1 e 2.3.6 criam um hotfix de botão de conta desativado
description: Este artigo fornece uma correção para o problema quando você luta para criar uma nova conta depois de inserir um valor incorreto em qualquer campo do formulário. Por exemplo, ao inserir um endereço de email no formato errado, deixar os campos de nome ou sobrenome vazios ou não inserir um valor que atenda aos requisitos de senha. Uma correção permanente será incluída nas versões do primeiro trimestre (2.4.2, 2.4.1-p1 e 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 e 2.3.6 criam um hotfix de botão de conta desativado

Este artigo fornece uma correção para o problema quando você luta para criar uma nova conta depois de inserir um valor incorreto em qualquer campo do formulário. Por exemplo, ao inserir um endereço de email no formato errado, deixar os campos de nome ou sobrenome vazios ou não inserir um valor que atenda aos requisitos de senha. Uma correção permanente será incluída nas versões do primeiro trimestre (2.4.2, 2.4.1-p1 e 2.3.6-p1).

## Problema

O botão **Criar uma Conta** na página **Criar Nova Conta** permanecerá desabilitado se um comprador tiver inserido dados inválidos. Isso impede que os compradores tentem criar uma conta novamente após cometer um erro.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Criar nova conta de cliente**.
1. Preencha os campos do formulário. No campo **Senha**, insira valores que não atendem aos requisitos de senha. Por exemplo:
   * As senhas nos campos **Senha** e **Confirmar Senha** não coincidem.
   * As senhas nos campos **Senha** e **Confirmar Senha** não são longas o suficiente.
1. Clique no botão **Criar uma Conta**.

<u>Resultados esperados</u>:

* O botão **Criar uma Conta** deve permanecer ativo/habilitado.
* O usuário deve conseguir criar uma nova conta.

<u>Resultados reais</u>:

* O botão **Criar uma Conta** permanece desabilitado, mesmo depois de preencher todos os campos obrigatórios com dados válidos/corretos.
* O cliente não pode criar uma nova conta.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no seguinte link: [Baixar MC-38509-composer.patch](assets/MC-38509-composer.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.3.6 e 2.4.1.
* Adobe Commerce no local 2.3.6 e 2.4.1.

O patch não é compatível com outras versões e edições do Adobe Commerce.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Leitura relacionada

* [GitHub Adobe Commerce > O envio de um formulário de criação de conta inválido deixa o botão de envio desativado](https://github.com/magento/magento2/issues/30513)
* [Guia do Usuário do Adobe Commerce > Introdução > Criando uma Conta](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create)
