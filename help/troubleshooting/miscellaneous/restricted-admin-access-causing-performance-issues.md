---
title: Acesso de administrador restrito que causa problemas de desempenho
description: Este artigo fornece soluções para quando o desempenho é afetado negativamente ao usar [Funções de administrador com escopo de função restrito pelo site](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) em nosso guia do usuário.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Acesso de administrador restrito que causa problemas de desempenho

Este artigo fornece soluções para situações em que o desempenho é afetado negativamente ao usar as [funções de Administrador com escopo de função restrito pelo site](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) em nosso guia do usuário.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x

## Problema

Quando um usuário administrador, com o escopo de função restrito pelo site, executa operações no painel Administrador (incluindo logon, salvamento de produtos e assim por diante), o Adobe Commerce recria o cache armazenado. A reconstrução do cache afeta negativamente o desempenho e pode levar a uma paralisação do site, especialmente durante horários comerciais e/ou de alto tráfego.

O problema foi corrigido no Adobe Commerce 2.2.10 e 2.3.3.

## Solução

A seguir estão as opções para evitar o problema:

* Atualize a versão do aplicativo do Adobe Commerce para 2.2.10 ou 2.3.3. (para obter instruções, consulte a [Atualização do Adobe Commerce na versão da infraestrutura em nuvem](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) em nossa documentação de desenvolvedor).
* Evite restringir o escopo da função de usuário Administrador por site, se possível.
* [Enviar um tíquete de Suporte Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), para solicitar um patch, se estiver disponível.

## Leitura relacionada

* [Funções do usuário](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/user-accounts/permissions-user-roles) em nosso guia do usuário.
