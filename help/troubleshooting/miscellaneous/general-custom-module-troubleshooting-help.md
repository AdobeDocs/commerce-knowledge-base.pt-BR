---
title: Ajuda geral para a solução de problemas do módulo personalizado
description: Este artigo fala sobre ferramentas gerais para ajudar na solução de problemas de módulos personalizados no Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Ajuda geral para a solução de problemas do módulo personalizado

Este artigo fala sobre ferramentas gerais para ajudar na solução de problemas de módulos personalizados no Adobe Commerce.

## Problema

Se você perceber que há um problema com os recursos do módulo personalizado e não receber mensagens de erro óbvias que declarem o problema, será necessário consultar os logs da instância.

## Solução

Verifique os logs para ver se há entradas com o nome do módulo personalizado no erro.  Dependendo dos erros envolvidos, a solução pode se apresentar ou talvez seja necessário incluir suas informações úteis de log do Adobe Commerce se você quiser abrir um [Tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consulte os parágrafos a seguir para obter informações sobre a localização dos logs e as possíveis soluções.

### Adobe Commerce (todos os métodos de implantação), Magento Open Source, todas as versões 2.X

1. Locais dos logs:
   * [Logs de arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem](/help/how-to/general/log-locations-directories-for-starter-plan.md) em nossa base de conhecimento de suporte.
   * [A arquitetura do plano Pro do Adobe Commerce na infraestrutura em nuvem registra](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) em nossa base de dados de conhecimento de suporte.
1. Dependendo dos erros encontrados, se você quiser ativar, desativar ou desinstalar um módulo personalizado, estes artigos detalham essas ações:
   * [Habilite ou desabilite os módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) na documentação do desenvolvedor.
   * [Desinstale os módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) da documentação do desenvolvedor.

### Adobe Commerce na infraestrutura em nuvem, todas as versões

1. Locais dos logs: [logs do Adobe Commerce em infraestrutura na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) em nossa documentação do desenvolvedor.
1. Dependendo dos erros encontrados, se você quiser ativar, desativar ou desinstalar um módulo personalizado, esses artigos em nossa documentação do desenvolvedor detalham essas ações:
   * [Instalar, gerenciar e atualizar extensões](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [Falha na implantação do componente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Visão geral do módulo](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Erros ao instalar dados de amostra opcionais](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [Manipulação de exceções](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [Exceções durante a instalação](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [Executar o Gerenciador de Módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [Arquivos de configuração de módulo](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)
* [Erros de memória insuficiente](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
