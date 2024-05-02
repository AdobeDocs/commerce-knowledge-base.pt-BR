---
title: Problemas de verificação de preparação do Cron
description: '"Este artigo fornece soluções para problemas de preparação do cron. Os seguintes são sintomas de problemas cron:'''
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Problemas de verificação de preparação do Cron

Este artigo fornece soluções para problemas de preparação do cron. A seguir estão os sintomas de problemas de cron:

* Uma mensagem de erro sobre a configuração do PHP `$HTTP_RAW_POST_DATA` é exibido mesmo se estiver definido corretamente.
* A verificação de preparação do PHP não exibe a versão do PHP como mostra a figura a seguir:
  ![up-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)
* O seguinte erro é exibido no Commerce Admin:
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
Para ver o erro, clique em **Mensagens do sistema** na parte superior da janela, como a seguir:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Verifique seu crontab existente {#check-your-existing-crontab}

Esta seção discute como ver se o CRON está em execução no momento e verificar se está configurado corretamente.

Para verificar se o crontab está configurado ou não:

1. Faça logon no servidor do Commerce como, ou alterne para, o [proprietário do sistema de arquivos Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Consulte se o seguinte arquivo existe: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Se o arquivo existir, o cron foi executado com sucesso no passado. Se o arquivo *não* existe, você ainda não instalou o Adobe Commerce ou o cron não está em execução. Em ambos os casos, continue com a próxima etapa.
1. Obtenha mais detalhes sobre cron. Como usuário com `root` insira o seguinte comando: `$ crontab -u <Magento file system owner name> -l`. Por exemplo, no CentOS `$ crontab -u magento_user -l`. Se nenhum crontab tiver sido configurado para o usuário, a seguinte mensagem será exibida:    `no crontab for magento_user`. Seu crontab lhe diz o seguinte:
   * Qual binário PHP você está usando (em alguns casos, você tem mais de um)
   * Quais scripts cron do Adobe Commerce você está executando (especificamente, os caminhos para esses scripts)
   * Onde estão localizados os logs CRON

   Consulte uma das seções a seguir para obter uma solução para o seu problema.

## Solução: crontab não está configurado {#solution-crontab-not-set-up}

Para verificar se os trabalhos cron estão configurados corretamente, consulte [Configurar trabalhos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) na documentação do desenvolvedor.

## Solução: cron executando a partir de binário PHP incorreto {#solution-cron-running-from-incorrect-php-binary}

Se o seu trabalho cron usa um binário PHP diferente do plug-in do servidor Web, erros de configuração de PHP podem ser exibidos. Para resolver o problema, defina configurações idênticas do PHP para a linha de comando do PHP e o plug-in do servidor Web PHP.

Para obter mais informações sobre as configurações do PHP, consulte [Configurações necessárias do PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) na documentação do desenvolvedor.

## Solução: cron em execução com erros {#solution-cron-running-with-errors}

Tente executar cada comando manualmente porque o comando pode exibir mensagens de erro úteis. Consulte [Configurar trabalhos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) na documentação do desenvolvedor.

>[!NOTE]
>
>Você deve executar o cron pelo menos *duas vezes* para que o job seja executado; a primeira vez que os jobs são enfileirados e a segunda vez que eles são executados.
