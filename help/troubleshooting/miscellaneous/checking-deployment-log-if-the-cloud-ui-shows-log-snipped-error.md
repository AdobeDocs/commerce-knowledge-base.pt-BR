---
title: Verificação do log de implantação se a interface do usuário da nuvem tiver um erro de "log recortado"
description: Este artigo fornece uma solução para o problema em que a interface do usuário do Adobe Commerce na infraestrutura em nuvem mostra a mensagem de erro *log recortado porque era muito longo* ao tentar exibir o log de implantação.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Verificação do log de implantação se a interface do usuário da nuvem tiver um erro de &quot;log recortado&quot;

Este artigo fornece uma solução para o problema em que a interface do usuário do Adobe Commerce na infraestrutura em nuvem mostra a *log recortado porque era muito longo* mensagem de erro ao tentar exibir o log de implantação.

## Produtos afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões compatíveis)

## Problema

Ao tentar exibir o log de implantação, a interface do usuário do Adobe Commerce na infraestrutura em nuvem mostra a seguinte mensagem de erro: *log recortado porque era muito longo*.

## Etapas a serem reproduzidas

1. Vá para o URL do projeto e clique no link **Status** da implantação em questão.
1. Se o log for muito longo para ser exibido na interface do usuário, ele mostrará a mensagem de erro: *log recortado porque era muito longo*.

## Causa

Observe que o log mostrado na interface do usuário não deve ser tratado como a fonte da verdade, especialmente se você descobrir que o site não está respondendo ou funcionando corretamente depois que a implantação foi listada com um status de Sucesso. Você também deve verificar os com os logs no servidor. Consulte [Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) na documentação do desenvolvedor.

## Solução

1. Verifique se você tem [CLI da Magento Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) instalado em seu ambiente local.
1. Execute o seguinte comando:

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. Ele retornará uma saída semelhante à seguinte:

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Copie a ID de atividade da implantação afetada e execute o comando:

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Exemplo para examinar o log da implantação com falha:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Leituras relacionadas em nossa documentação do desenvolvedor:

* [Adobe Commerce na infraestrutura em nuvem > Criar e implantar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [Adobe Commerce na infraestrutura em nuvem > Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
