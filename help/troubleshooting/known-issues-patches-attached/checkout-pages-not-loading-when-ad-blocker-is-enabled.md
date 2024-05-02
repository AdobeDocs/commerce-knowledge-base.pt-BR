---
title: As páginas de check-out não são carregadas quando o bloqueador de anúncios está ativado
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.2 relacionado à falha ao carregar páginas de check-out causada pelo uBlock ou outros bloqueadores de anúncios.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# As páginas de check-out não são carregadas quando o bloqueador de anúncios está ativado

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.2 relacionado à falha ao carregar páginas de check-out causada pelo uBlock ou outros bloqueadores de anúncios.

## Problema

Se o Google Analytics estiver ativado para a loja, quando um cliente com uBlock instalado ou outro bloqueador de anúncios prosseguir para a finalização, a variável `trackingCode.js` O arquivo está bloqueado para carregamento e RequireJS interrompe o fluxo de execução JS. Isso causa problemas com o carregamento da página de check-out.

<u>Etapas a serem reproduzidas</u> :

Pré-requisitos: um bloqueador de anúncios deve estar instalado e ativo no navegador.

1. No Administrador do Commerce, ative e configure a funcionalidade Google Analytics.
1. Abra uma página de produto na loja.
1. Adicione produtos ao carrinho.
1. Clique em **Ir para Check-out** link.

<u>Resultado esperado</u>: a página de Check-out é carregada e o cliente pode concluir o check-out.

<u>Resultado real</u>: a página de check-out não carrega; o ponteiro de carregamento nunca desaparece.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-9353\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.2

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem de 2.1.0 para 2.1.14
* Adobe Commerce na infraestrutura em nuvem de 2.2.0 para 2.2.1 e 2.2.3 para 2.2.5
* Adobe Commerce no local, de 2.1.0 a 2.1.14
* Adobe Commerce no local, de 2.2.0 para 2.2.5

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de conhecimento de suporte.

## Links úteis

* [O problema foi discutido no GitHub](https://github.com/magento/magento2/pull/13061)

## Arquivos Anexados
