---
title: Solução de problemas do CRON
description: Este artigo oferece soluções de problemas com o cron em produtos Adobe Commerce no local.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: b6a79bcff3d757d40e7070182d8853a37960a782
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Solução de problemas do CRON

Este artigo oferece soluções de problemas com o cron em produtos Adobe Commerce no local.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problemas

## A seguir estão os sintomas de problemas de cron:

* Sua atualização nunca é executada; ela permanece em um `pending` estado.
* Uma mensagem de erro sobre o [PHP](https://glossary.magento.com/php) configuração `$HTTP_RAW_POST_DATA` é exibido mesmo se estiver definido corretamente.
* Falha na verificação de preparação do cron. Os possíveis erros incluem caminhos não graváveis e cron não configurado. Um exemplo é o seguinte:

  ![up-tshoot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* A verificação de preparação do PHP não exibe a versão do PHP como mostra a figura a seguir.

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* O seguinte erro é exibido no Commerce Admin:

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

Para ver o erro, clique em **Mensagens do sistema** na parte superior da janela, como a seguir:

![compman_sys-messages.png](assets/compman_sys-messages.png)

## Investigue para encontrar a causa {#check-your-existing-crontab}

Esta seção discute como ver se o cron está em execução no momento e como verificar se ele está configurado corretamente.

Para verificar se o crontab está ou não configurado, siga estas etapas:

1. Efetue login no servidor Magento como ou alterne para o [proprietário do sistema de arquivos Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Consulte se o seguinte arquivo existe:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Se o arquivo existir, o cron foi executado com sucesso no passado. Se o arquivo *não* existe, você ainda não instalou o Magento ou o cron não está em execução. Em ambos os casos, continue com a próxima etapa.
1. Obtenha mais detalhes sobre cron. Como usuário com `root` insira o seguinte comando:    `bash    crontab -u <Magento file system owner name> -l`. Por exemplo, no CentOS `bash    crontab -u magento_user -l`.  Se nenhum crontab tiver sido configurado para o usuário, a seguinte mensagem será exibida:    `terminal    no crontab for magento_user`. Seu crontab lhe diz o seguinte:

   * Qual binário PHP você está usando (em alguns casos, você tem mais de um)
   * Quais scripts Magento cron você está executando (especificamente, os caminhos para esses scripts)
   * Onde estão localizados os logs CRON

Consulte uma das seções a seguir para obter uma solução para o seu problema.

## Soluções

### Solução para crontab não está sendo configurada {#solution-crontab-not-set-up}

Para verificar se os trabalhos cron estão configurados corretamente, consulte [Configurar trabalhos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

### Solução para cron executado a partir de binário PHP incorreto {#solution-cron-running-from-incorrect-php-binary}

Se o seu trabalho cron usa um binário PHP diferente do plug-in do servidor Web, erros de configuração de PHP podem ser exibidos. Para resolver o problema, defina configurações idênticas do PHP para a linha de comando do PHP e o plug-in do servidor Web PHP.

Para obter mais informações sobre as configurações do PHP, consulte [Configurações necessárias do PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) na documentação do desenvolvedor.

### Solução para cron em execução com erros {#solution-cron-running-with-errors}

Tente executar cada comando manualmente porque o comando pode exibir mensagens de erro úteis. Consulte [Configurar trabalhos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

>[!NOTE]
>
>Você deve executar o cron pelo menos *duas vezes* para que o job seja executado; a primeira vez que os jobs são enfileirados e a segunda vez que eles são executados.
