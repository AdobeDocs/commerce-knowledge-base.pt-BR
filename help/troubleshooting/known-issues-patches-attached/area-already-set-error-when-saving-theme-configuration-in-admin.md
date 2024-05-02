---
title: Erro "Área já definida" ao salvar a configuração do tema no Administrador
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.4 relacionado à obtenção da mensagem de erro *"A área já está definida"* ao tentar definir um tema para a Exibição de loja padrão no Administrador do Commerce.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Erro &quot;Área já definida&quot; ao salvar a configuração do tema no Administrador

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.4 relacionado à obtenção do *&quot;A área já está definida&quot;* mensagem de erro ao tentar definir um tema para a Exibição de loja padrão no Administrador do Commerce.

## Problema

Você obtém o &quot; *Ocorreu um problema ao salvar esta configuração: a área já está definida* &quot;mensagem de erro ao tentar definir um tema para a Exibição de loja padrão.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce.
1. Navegue até **Conteúdo** > **Design** > **Configuração**.
1. Defina o escopo de configuração como *Visualização da loja padrão*.
1. Alterar o tema no **Tema aplicado** menu suspenso. Por exemplo, de *Luma* para *Em branco.*
1. Clique em **Salvar configuração**.

<u>Resultado esperado</u>: o tema selecionado é aplicado à exibição de loja padrão.

<u>Resultado real</u> : o tema não é aplicado, o parâmetro *&quot;Algo deu errado ao salvar esta configuração: a área já está definida&quot;* é exibida.

## Correção

O patch está anexado a este artigo. Para baixá-lo, clique no link a seguir ou role para baixo até o final do artigo e clique no arquivo anexado:

[Baixar MDVA-11106\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.4

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.0.X
* Adobe Commerce na infraestrutura em nuvem 2.1.X
* Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.5
* Adobe Commerce no local 2.0.X
* Adobe Commerce no local 2.1.X
* Adobe Commerce no local 2.2.0 - 2.2.5

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de conhecimento de suporte.

## Arquivos Anexados
