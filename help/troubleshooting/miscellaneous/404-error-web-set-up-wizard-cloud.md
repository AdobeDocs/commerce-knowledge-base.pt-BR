---
title: Erro 404 não encontrado ao acessar o Assistente para configuração da Web por meio do painel de Administração
description: Este artigo fornece uma solução para quando ocorrer um erro 404 não encontrado ao tentar acessar o Assistente de configuração da Web por meio do painel de administração.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Erro 404 não encontrado ao acessar o Assistente para configuração da Web por meio do painel de Administração

Este artigo fornece uma solução para quando ocorrer um erro 404 não encontrado ao tentar acessar o Assistente de configuração da Web por meio do painel de administração.

## Produtos e versões afetados

* A funcionalidade do Assistente de configuração da Web foi substituída na Adobe Commerce (todos os métodos de implantação) 2.3.6 e removida na 2.4.0.

## Problema

Ao instalar uma extensão usando o Assistente de configuração da Web, uma página 404 é exibida.

<u>Etapas a serem reproduzidas</u>:

O comerciante clica no Assistente de configuração da Web para instalar um novo módulo/integração.

<u>Resultado esperado</u>:

Instalações de módulo/integração.

<u>Resultado real</u>:

Um erro 404 é exibido.

## Causa

O Assistente de Configuração da Web foi desabilitado para todas as instâncias do Adobe Commerce na infraestrutura em nuvem; não é possível habilitá-lo. As extensões devem ser instaladas por meio do Composer.

## Solução

Esse recurso está desabilitado no Adobe Commerce na infraestrutura em nuvem.

Consulte [Instalar, gerenciar e atualizar extensões](https://devdocs.magento.com/cloud/howtos/install-components.html) na documentação do desenvolvedor, para obter informações sobre como executar atualizações ou instalar módulos externos para o Adobe Commerce em nossa infraestrutura em nuvem.
Consulte [Instalação de início rápido](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) na documentação do desenvolvedor, para obter informações sobre como executar atualizações ou instalar módulos externos para o Adobe Commerce no local.

## Leitura relacionada

* Consulte [Instalar uma extensão](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension) na documentação do desenvolvedor.
