---
title: Verificação do log de implantação se a interface do usuário da nuvem tiver um erro de "log recortado"
description: Este artigo fornece uma solução para o problema em que a interface do usuário do Adobe Commerce na infraestrutura em nuvem mostra a mensagem de erro *log recortado porque era muito longo* ao tentar exibir o log de implantação na interface do usuário do projeto em nuvem.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%
---
# Verificando o log de implantação se a interface da nuvem tem o erro *log recortado*

Este artigo fornece uma solução para o problema em que o Adobe Commerce na interface do usuário da infraestrutura em nuvem mostra a mensagem de erro *log recortado porque era muito longo* ao tentar exibir o log de implantação na interface do usuário do projeto em nuvem. (Não se aplica ao [Console da Adobe Commerce Cloud](https://console.adobecommerce.com/).)

## Produtos afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões compatíveis)

## Problema

Ao tentar exibir o log de implantação na interface do projeto de nuvem, o Adobe Commerce na interface da infraestrutura de nuvem mostra a seguinte mensagem de erro: *log interrompido porque era muito longo*.

## Etapas a serem reproduzidas

1. Vá para a URL do Projeto e clique no **Status** da implantação em questão.
1. Se o log for muito longo para ser exibido na interface, ele mostrará a mensagem de erro: *log cortado porque era muito longo*.

## Causa

Observe que o log mostrado na interface do usuário não deve ser tratado como a fonte da verdade, especialmente se você descobrir que o site não está respondendo ou funcionando corretamente depois que a implantação foi listada com um status de Sucesso. Você também deve verificar os com os logs no servidor. Consulte [Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=pt-BR) na documentação do desenvolvedor.

## Solução

1. Verifique se você tem a [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=pt-BR) instalada em seu ambiente local.
1. Você pode executar um dos comandos a seguir:

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. Eles retornarão uma saída semelhante à seguinte:

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

* [Adobe Commerce na infraestrutura em nuvem > Criar e implantar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=pt-BR)
* [Adobe Commerce na infraestrutura em nuvem > Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=pt-BR)
