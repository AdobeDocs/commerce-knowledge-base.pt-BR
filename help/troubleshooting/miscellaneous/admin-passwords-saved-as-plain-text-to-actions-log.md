---
title: Senhas de administrador salvas como texto sem formatação no log de ações
description: Este artigo fornece uma correção para quando um Administrador do Commerce cria um novo usuário com privilégios de Administrador e a senha é salva como texto sem formatação na tabela de banco de dados "magento_logging_event_changes".
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Senhas de administrador salvas como texto sem formatação no log de ações

Este artigo fornece uma correção para quando um Administrador do Commerce cria um novo usuário com privilégios de Administrador e a senha é salva como texto simples na tabela de banco de dados `magento_logging_event_changes`.

Para corrigir esse problema de segurança, instale a Atualização de segurança do Adobe Commerce 2.0.16 e 2.1.9. Após aplicar a Atualização de segurança, as senhas são criptografadas e não aparecem como texto simples.

## Versões afetadas {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce no local 2.X.X
* Adobe Commerce na infraestrutura em nuvem 2.X.X

## Problema {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Quando um Administrador do Commerce existente cria um novo usuário com privilégios de Administrador via **Sistema** > **Permissões** > **Todos os usuários** > **Adicionar novo usuário**, a senha (inserida como confirmação) é salva como texto sem formatação na tabela de banco de dados `magento_logging_event_changes`.

### Etapas a serem reproduzidas: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Faça logon como Administrador e crie um novo usuário navegando até este caminho: **Sistema** > Permissões > **Todos os usuários**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Depois clique na página **Adicionar novo usuário**. Quando solicitado, forneça sua senha de administrador atual.
1. Vá para a página **Sistema** > **Log de Ações** > **Relatório** e localize a última entrada do log.
1. Você pode ver a senha atual, não criptografada nem com hash.

## Solução {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

A instalação da [Atualização de Segurança do Adobe Commerce 2.0.16 e 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) corrige esse problema.

Depois de instalar a Atualização de Segurança, a senha é criptografada e não é exibida em texto sem formatação na tabela `magento_logging_event_changes`.

## Mais informações {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

* [Página de Atualização de Segurança do Adobe Commerce 2.0.16 e 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) na nossa central de segurança
* [Atualize o aplicativo e os componentes do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) em nossa documentação do desenvolvedor
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
