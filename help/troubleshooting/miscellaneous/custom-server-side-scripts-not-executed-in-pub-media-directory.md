---
title: Os scripts personalizados do lado do servidor não são executados no diretório de mídia pub
description: Este artigo fornece uma correção para quando os scripts personalizados do lado do servidor não são executados se colocados em `.diretório /pub/media/` do aplicativo do Adobe Commerce na infraestrutura em nuvem. Essa é uma limitação de segurança esperada, desde que o ".O diretório /pub/media/` é gravável. Para tornar os scripts executáveis, coloque-os em diretórios não graváveis, como `./app/code/` ou `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Os scripts personalizados do lado do servidor não são executados no diretório de mídia pub

Este artigo fornece uma correção para quando scripts personalizados do lado do servidor não são executados se forem colocados no diretório `./pub/media/` de seu aplicativo Adobe Commerce na infraestrutura da nuvem. Esta é uma limitação de segurança esperada, pois o diretório `./pub/media/` é gravável. Para tornar os scripts executáveis, coloque-os em diretórios não graváveis, como `./app/code/` ou `./pub/`.

## Versões afetadas

* Adobe Commerce na infraestrutura em nuvem: 2.1.x e posterior, Starter e Pro planeja arquiteturas, Wings e herdadas

## Problema: scripts não executados

Os scripts personalizados do lado do servidor não podem ser executados quando iniciados.

Por exemplo, quando o usuário final (comprador do Adobe Commerce) clica no link que leva ao arquivo `\*.php` com o script (como *domain.com/media/directory/script.php* ), o script está sendo baixado em vez de ser executado.

## Causa: local incorreto do arquivo de script

O problema ocorre quando os arquivos de script estão localizados no diretório `./pub/media/` do aplicativo Adobe Commerce na infraestrutura em nuvem. Este é um comportamento esperado: devido a limitações de segurança, os arquivos dos diretórios graváveis (`./pub/media/`) nunca são executados.

## Solução: coloque scripts em diretórios não graváveis

Armazene os scripts do lado do servidor em diretórios não graváveis, como `./app/code/` ou `./pub/` &quot;

## Documentação relacionada

* [Nuvem para Adobe Commerce > Estrutura de projeto > Diretórios graváveis](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) em nossa documentação do desenvolvedor.
