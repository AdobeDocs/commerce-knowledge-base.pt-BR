---
title: "B2B: As empresas não podem acessar páginas de perfil na loja"
description: Este artigo fornece um patch para o problema B2B conhecido do Adobe Commerce 2.2.4 relacionado às empresas registradas que recebem erros em suas páginas de conta na loja.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: As empresas não podem acessar páginas de perfil na loja

Este artigo fornece um patch para o problema B2B conhecido do Adobe Commerce 2.2.4 relacionado às empresas registradas que recebem erros em suas páginas de conta na loja.

## Problema

Os clientes (empresas) podem criar uma conta de empresa com êxito no site, mas recebem as mensagens de erro *&quot;Nenhuma entidade com customerId = &quot;* e *&quot;Você ainda não tem uma conta de empresa&quot;*. Eles também podem receber o *&quot;Erro interno de servidor 500&quot;* ao tentar acessar a página Perfil da empresa.

## Correção

Para baixar o arquivo com um patch, clique no link a seguir:

[Baixar MDVA-9013\_EE\_2.2.2\_composer.patch](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Versões compatíveis do Adobe Commerce

A correção foi criada para:

* Adobe Commerce no local 2.2.2

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem de 2.2.0 para 2.2.4
* Adobe Commerce no local, de 2.2.0 para 2.2.1 e de 2.2.3 para 2.2.4

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.
