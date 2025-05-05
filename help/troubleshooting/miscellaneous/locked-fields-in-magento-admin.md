---
title: Campos bloqueados (esmaecidos) no Commerce Admin
description: Este artigo fornece uma solução para quando não é possível modificar campos no Administrador do Commerce.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Campos bloqueados (esmaecidos) no Commerce Admin

Este artigo fornece uma solução para quando não for possível modificar campos bloqueados (esmaecidos) no Administrador do Commerce.

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

* [Exporte a Configuração](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration) na documentação do desenvolvedor.
* [Definir valores de Configuração](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values) na documentação do desenvolvedor.
* [Adobe Commerce na infraestrutura em nuvem: reduza o tempo de inatividade da implantação com o Gerenciamento de Configuração](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) em nossa base de conhecimento de suporte.
