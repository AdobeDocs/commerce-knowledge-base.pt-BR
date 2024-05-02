---
title: Erro ao ativar a otimização de imagem no Adobe Commerce
description: Este artigo fornece uma solução para o problema em que o Fastly Image Otimization (IO) é desativado por padrão com uma notificação para entrar em contato com o Fastly para ativar a otimização da imagem. (O Fastly Cloud Image Otimizer é um serviço de manipulação e otimização de imagens em tempo real que acelera a entrega de imagens, disponibilizando imagens com eficiência de largura de banda.)
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Erro ao ativar a otimização de imagem no Adobe Commerce

Este artigo fornece uma solução para o problema em que o Fastly Image Otimization (IO) é desativado por padrão com uma notificação para entrar em contato com o Fastly para ativar a otimização da imagem. (O Fastly Cloud Image Otimizer é um serviço de manipulação e otimização de imagens em tempo real que acelera a entrega de imagens, disponibilizando imagens com eficiência de largura de banda.)

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x

## Problema

Na página Configuração do Fastly, ao lado do Fragmento do Fastly IO, você vê o estado Atual: \_disabled \_with a seguinte mensagem abaixo: Entre em contato com seu representante de vendas ou envie um email para `support@fastly.com` para solicitar a ativação de otimização de imagem para o serviço Fastly.

## Causa

O site pode não estar ativo ainda. Existem processos em vigor para pré-carregar o site quando ele for colocado no banco de dados do Fastly.

## Solução

Criar um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e solicitar otimização de imagem.
