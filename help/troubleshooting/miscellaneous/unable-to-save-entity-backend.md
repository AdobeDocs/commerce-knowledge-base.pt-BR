---
title: Não é possível salvar o back-end do Adobe Commerce da entidade
description: Este artigo fornece uma solução para quando não for possível salvar uma entidade no back-end do Adobe Commerce. Por exemplo, quando não é possível editar e salvar uma regra específica de "cart_price".
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Não é possível salvar o back-end do Adobe Commerce da entidade

Este artigo fornece uma solução para quando não for possível salvar uma entidade no back-end do Adobe Commerce. Por exemplo, quando não é possível editar e salvar uma regra `cart_price` específica.

## Produtos e versões afetados

Esse problema pode afetar todas as versões do Adobe Commerce que têm o Tamanho máximo de sessão configurado. Isso foi adicionado a partir do Magento Open Source 2.3.7-p1 e do Adobe commerce (todos os métodos de implantação) 2.4.3.


## Problema

Quando você tenta reconfigurar seu armazenamento, a página é recarregada e suas alterações não são salvas. Uma mensagem pode ser vista em `var/log/system.log`:

*[2021-11-27 00:30:52] report.WARNING: O tamanho de sessão 418056 excedeu o tamanho máximo de sessão permitido de 256000. [][]*

<u>Etapas a serem reproduzidas</u>:

Um exemplo de configuração de armazenamento que não está sendo salva:

1. Selecione uma regra no Adobe Commerce Store em Produção > **Marketing** > **Regras de preço do carrinho**.
1. Escolha uma regra e defina como *Inativo* e salve a alteração.

<u>Resultado esperado</u>:

A regra está definida como inativa.

<u>Resultado real</u>:

* Recarrega a página sem nenhuma mensagem.
* A regra ainda está definida como ativa.

## Causa

Esse problema está relacionado à nova funcionalidade introduzida recentemente que afetou o Tamanho máximo da sessão. Consulte [Gerenciamento de sessão](https://docs.magento.com/user-guide/stores/security-session-management.html) na documentação do desenvolvedor.

## Solução

Aumente o valor de &quot;Tamanho Máximo da Sessão&quot; em (**Lojas** > **Configuração** > **Avançado** > **Sistema** > **Segurança** > Tamanho Máximo da Sessão).

## Leitura relacionada

* [Menu de marketing](https://docs.magento.com/user-guide/marketing/marketing-menu.html) em nosso guia do usuário.
