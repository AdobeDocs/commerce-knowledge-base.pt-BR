---
title: Email do pedido enviado do endereço de email do servidor
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.4 relacionado ao envio de emails de pedido do endereço de email do servidor.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Email do pedido enviado do endereço de email do servidor

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.4 relacionado ao envio de emails de pedido do endereço de email do servidor.

## Problema

Os emails de confirmação de pedido são enviados pelo endereço de email do servidor Apache. Outros emails (senha esquecida e assim por diante) são enviados dos endereços de email configurados.

<u>Etapas a serem reproduzidas</u>:

1. Fazer um pedido com a **Enviar confirmação do pedido** caixa marcada.
1. Verifique o email.

<u>Resultado esperado</u>:

O email foi enviado do endereço de envio configurado pela Adobe Commerce.

<u>Resultado real</u>:

O email foi enviado do endereço de email configurado no servidor Apache que está sendo usado.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-10993\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.4

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Infraestrutura do Adobe Commerce na nuvem 2.2.5
* Infraestrutura do Adobe Commerce na nuvem 2.2.6
* Infraestrutura do Adobe Commerce na nuvem 2.2.7
* Infraestrutura do Adobe Commerce na nuvem 2.2.8
* Adobe Commerce no local 2.2.4
* Adobe Commerce no local 2.2.5
* Adobe Commerce no local 2.2.6
* Adobe Commerce no local 2.2.7
* Adobe Commerce no local 2.2.8
* Adobe Commerce no local 2.3.0

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de conhecimento de suporte.

## Arquivos Anexados
