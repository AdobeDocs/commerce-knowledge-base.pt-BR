---
title: Erro ao fazer logon no Commerce Admin
description: Este artigo fornece uma solução para o problema em que você recebe uma mensagem de erro informando que o URL solicitado não foi encontrado neste servidor.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Erro ao fazer logon no Commerce Admin

Este artigo fornece uma solução para o problema em que você recebe uma mensagem de erro informando que o URL solicitado não foi encontrado neste servidor.

## Detalhes

O URL solicitado /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ não foi encontrado neste servidor.

Observe a falta de um caractere de barra entre `magento2` e `index.php` na URL.

## Solução

O URL de base não está correto. O URL de base deve:

* Iniciar com `http://` ou `https://`
* Termina com uma barra ( `/` )
* Corresponder letras maiúsculas e minúsculas do registro `web/unsecure/base_url` na tabela de banco de dados `core_config_data`

Execute a instalação novamente usando um valor válido.

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
