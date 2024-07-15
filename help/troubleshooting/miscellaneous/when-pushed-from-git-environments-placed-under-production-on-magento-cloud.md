---
title: Novos ambientes colocados em produção quando enviados do Git
description: Este artigo fornece uma solução para o problema em que novos ambientes são colocados no ambiente de produção no Adobe Commerce na infraestrutura em nuvem quando enviados do sistema de controle de versão Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Novos ambientes colocados em produção quando enviados do Git

Este artigo fornece uma solução para o problema em que novos ambientes são colocados no ambiente de produção no Adobe Commerce na infraestrutura em nuvem quando enviados do sistema de controle de versão Git.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Pré-requisitos</u>:

Ter um clone Git controlado do projeto.

<u>Etapas a serem reproduzidas</u>:

Você precisa criar uma ramificação de integração a partir da ramificação de preparo:

1. Alterne para a ramificação de preparo executando o seguinte comando no shell local: `git checkout staging`
1. Crie uma ramificação de integração a partir da ramificação de preparo executando o seguinte comando no shell local: `git checkout -b <branch>`
1. Envie a ramificação para o repositório remoto e configure uma ramificação upstream executando o seguinte comando no shell local: `git push --set-upstream origin <branch>`

<u>Resultados esperados</u>:

A nova ramificação é criada na ramificação de preparo.

<u>Resultados reais</u>:

A nova filial foi criada na ramificação de produção.

## Causa

Isso não é um erro. Para configurar uma filial principal para outra filial, o comerciante deve usar a CLI da magento-cloud.

## Solução

Uma ramificação pai só pode ser definida depois que o comerciante enviou uma ramificação recém-criada e a ativou. Consulte [Adobe Commerce na infraestrutura da nuvem > Integração do Bitbucket](https://devdocs.magento.com/cloud/integrations/bitbucket-integration.html#create-a-new-cloud-branch) em nossa documentação de desenvolvedor.

Para atualizar um pai para a ramificação existente no servidor, use o comando `magento-cloud environment:info` na CLI da magento-cloud.

Exemplo de uso:

`magento-cloud environment:info parent Staging`

Isso definirá a ramificação principal como &quot;Preparo&quot; para a ramificação atualmente com check-out.

## Leitura relacionada

* [Adobe Commerce na infraestrutura da nuvem > magento-cloud CLI](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html) na documentação do desenvolvedor.
