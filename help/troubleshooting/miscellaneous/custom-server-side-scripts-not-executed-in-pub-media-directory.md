---
title: Os scripts personalizados do lado do servidor não são executados no diretório de mídia pub
description: Este artigo fornece uma correção para quando os scripts personalizados do lado do servidor não são executados se colocados no diretório "./pub/media/" do aplicativo do Adobe Commerce na infraestrutura da nuvem. Essa é uma limitação de segurança esperada, pois o diretório "./pub/media/" é gravável. Para tornar os scripts executáveis, coloque-os em diretórios não graváveis, como "./app/code/" ou "./pub/".
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '284'
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

* [Nuvem para Adobe Commerce > Estrutura de projeto > Diretórios graváveis](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) em nossa documentação do desenvolvedor.
