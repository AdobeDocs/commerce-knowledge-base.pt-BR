---
title: Erro ao fazer logon no Commerce Admin
description: Este artigo fornece uma solução para o problema em que você recebe uma mensagem de erro informando que o URL solicitado não foi encontrado neste servidor.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '166'
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

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
