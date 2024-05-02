---
title: Ajuda geral para a solução de problemas do módulo personalizado
description: Este artigo fala sobre ferramentas gerais para ajudar na solução de problemas de módulos personalizados no Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Ajuda geral para a solução de problemas do módulo personalizado

Este artigo fala sobre ferramentas gerais para ajudar na solução de problemas de módulos personalizados no Adobe Commerce.

## Problema

Se você perceber que há um problema com os recursos do módulo personalizado e não receber mensagens de erro óbvias que declarem o problema, será necessário consultar os logs da instância.

## Solução

Verifique os logs para ver se há entradas com o nome do módulo personalizado no erro.  Dependendo dos erros envolvidos, a solução pode se apresentar ou talvez seja necessário incluir suas informações de log úteis do Adobe Commerce se você quiser abrir um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consulte os parágrafos a seguir para obter informações sobre a localização dos logs e as possíveis soluções.

### Adobe Commerce (todos os métodos de implantação), Magento Open Source, todas as versões 2.X

1. Locais dos logs:
   * [Logs de arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem](/help/how-to/general/log-locations-directories-for-starter-plan.md) em nossa base de conhecimento de suporte.
   * [Logs de arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) em nossa base de conhecimento de suporte.
1. Dependendo dos erros encontrados, se você quiser ativar, desativar ou desinstalar um módulo personalizado, estes artigos detalham essas ações:
   * [Ativar ou desativar módulos](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) na documentação do desenvolvedor.
   * [Desinstalar módulos](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) na documentação do desenvolvedor.

### Adobe Commerce na infraestrutura em nuvem, todas as versões

1. Locais dos logs: [Adobe Commerce em logs de infraestrutura em nuvem](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) na documentação do desenvolvedor.
1. Dependendo dos erros encontrados, se você quiser ativar, desativar ou desinstalar um módulo personalizado, esses artigos em nossa documentação do desenvolvedor detalham essas ações:
   * [Instalar, gerenciar e atualizar extensões](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Falha na implantação do componente](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Visão geral do módulo](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Erros ao instalar dados de amostra opcionais](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Tratamento de exceções](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Exceções durante a instalação](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Execute o Gerenciador de módulos](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [Arquivos de configuração de módulo](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Erros de falta de memória](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
