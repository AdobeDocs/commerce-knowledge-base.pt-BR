---
title: Campos bloqueados no administrador do Commerce
description: Este artigo fornece uma solução para quando não é possível modificar campos no Administrador do Commerce.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Campos bloqueados no administrador do Commerce

Este artigo fornece uma solução para quando não é possível modificar campos no Administrador do Commerce.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.x, 2.4.x
* Adobe Commerce na infraestrutura em nuvem 2.3.x, 2.4.x

## Problema

Depois que você salvar uma alteração na sua configuração para `app/etc/env.php` ou `app/etc/config.php`, não será possível modificar a configuração no Administrador.

<u>Etapas a serem reproduzidas</u>:

Observação: este é um exemplo - o problema pode afetar todas as configurações que foram salvas.

1. O comerciante salva suas credenciais de métodos de entrega usando o seguinte comando no terminal: `./vendor/bin/ece-tools config:dump`. Isso salva as credenciais no arquivo `app/etc/env.php`.
1. O comerciante tenta alterar as credenciais posteriormente.

<u>Resultados esperados</u>:

O comerciante pode definir os valores nas configurações do campo Admin e salvá-los.

<u>Resultados reais</u>:

Os campos no Admin estão bloqueados ou os valores podem ser alterados, mas não serão salvos no Admin.

## Causa

Quando a configuração for salva em `env.php` ou `config.php`, você não poderá modificar a configuração no Administrador. Para permitir a edição da configuração, você terá que remover a configuração de `env.php` ou `config.php`.

## Solução

Verifique se a configuração não foi salva em `app/etc/env.php` ou `app/etc/config.php`. Se ele tiver sido salvo, tente as seguintes etapas:

* `config.php` - Remover a configuração e reimplantar.
* `env.php` - Modificar diretamente no servidor, remover a configuração e executar `bin/magento app:config:import`.

## Leitura relacionada

* [Exporte a Configuração](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) na documentação do desenvolvedor.
* [Definir valores de Configuração](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) na documentação do desenvolvedor.
* [Adobe Commerce na infraestrutura em nuvem: reduza o tempo de inatividade da implantação com o Gerenciamento de Configuração](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) em nossa base de conhecimento de suporte.
