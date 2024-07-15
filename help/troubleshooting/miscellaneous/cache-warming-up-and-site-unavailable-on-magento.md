---
title: Aquecimento de cache e site indisponível no Adobe Commerce
description: Este artigo fornece uma solução para quando o cache da página estiver aquecendo e houver uma implantação paralisada ou site inativo.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Aquecimento de cache e site indisponível no Adobe Commerce

Este artigo fornece uma solução para quando o cache da página estiver aquecendo e houver uma implantação paralisada ou site inativo.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

O script de aquecimento de cache, no final da fase de pós-implantação, envia solicitações a uma taxa tão alta que determinadas instâncias, como as de 4 cpu, não podem lidar com isso. O nginx deles esgota o número de trabalhadores.

<u>Etapas a serem reproduzidas</u>:

Iniciar operações de aquecimento do cache.

<u>Resultado esperado</u>:

Páginas ou todo o site é carregado.

<u>Resultado real</u>:

O site não está disponível ou o tempo de resposta é muito alto.

## Solução

Limitar o número de conexões simultâneas durante o aquecimento do cache. Isso requer a adição da variável de pós-implantação `WARM_UP_CONCURRENCY` para especificar o número de solicitações de aquecimento que o script de aquecimento de cache pode enviar simultaneamente. Definir essa opção pode ajudar a gerenciar a carga na infraestrutura em nuvem da Adobe Commerce. Para ver as etapas, consulte [Post-deploy variables > WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency) na documentação do desenvolvedor.

## Leitura relacionada

[Cache de Página Inteira](https://docs.magento.com/user-guide/system/cache-full-page.html) em nosso guia do usuário
