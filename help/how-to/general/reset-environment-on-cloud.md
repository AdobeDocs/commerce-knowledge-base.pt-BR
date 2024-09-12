---
title: Redefinir o ambiente no Adobe Commerce na infraestrutura em nuvem
description: Este artigo mostra diferentes cenários de reversão de um ambiente no Adobe Commerce na infraestrutura em nuvem.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 598459365cad811966ed529356cb9ab876f49a38
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# Redefinir o ambiente no Adobe Commerce na infraestrutura em nuvem

Este artigo mostra diferentes cenários de reversão de um ambiente no Adobe Commerce na infraestrutura em nuvem.

Escolha o mais apropriado para seu caso:

* Se você tiver uma atividade planejada (implantação ou atualização planejada) - [Cenário 1: atividade planejada)](#scen1).
* Se você tiver um instantâneo válido - [Cenário 2: restaurar um instantâneo](#scen2).
* Se você tiver uma compilação estável, mas nenhum instantâneo válido - [Cenário 3: nenhum instantâneo, compilação estável (conexão SSH disponível)](#scen3).
* Se a compilação for interrompida e você não tiver um instantâneo válido - [Cenário 4: nenhum instantâneo; compilação interrompida (sem conexão SSH)](#scen4).

## Cenário 1: atividade planejada

Com uma implantação ou atualização planejada, o [!UICONTROL Rollback] mais fácil e recomendado seria para o comerciante, como parte de suas preparações, fazer o seguinte:

>[!NOTE]
>
>Sempre teste essas etapas no **[!UICONTROL Staging Environment]** primeiro!

<u>Cinco dias antes das atividades de atualização/implantação</u>:

1. Verifique o tamanho do Banco de Dados atual.
1. Verifique se há espaço em disco suficiente em `/data/exports` para conter um [!UICONTROL Database Dump]. Se não houver espaço em disco suficiente, remova os dados indesejados ou crie um caso de suporte e solicite a expansão do disco.

<u>No dia das alterações</u>:

1. Colocar o site em [!UICONTROL Maintenance Mode].
Leia mais sobre [Habilitar ou desabilitar [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) em nosso guia do usuário e [[!UICONTROL Maintenance Mode] opções de atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) em nosso guia de atualização.
1. Desabilitar trabalhos cron. Leia mais sobre como desabilitar trabalhos cron em nosso [guia de propriedades de cron](<https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>).
1. Pegue um [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html) local.

<u>Se [!UICONTROL Rollback] for necessário</u>:

1. Se aplicativos como o [!DNL MariaDB] tiverem sido atualizados como parte dessa atividade planejada, primeiro instale esse aplicativo em uma versão anterior.
1. [!UICONTROL Rollback] o Banco de Dados usando o [!UICONTROL Database Dump] local e importe-o de volta para [!DNL MariaDB].
1. [!UICONTROL Rollback] o código via [!DNL Git] para uma versão anterior em funcionamento.

O uso de [!UICONTROL Snapshots] não é a maneira recomendada para a atividade de atualização/planejada [!UICONTROL rollbacks/restores], pois demora muito mais para recuperar os dados do que um [!UICONTROL Database Dump] local, conforme descrito acima na Etapa 2 da seção **Se um [!UICONTROL Rollback] for necessário**.

[!UICONTROL Snapshots] não são mantidos no nó/servidor, são mantidos em um bloco de armazenamento separado e, como esses dados devem ser transmitidos do armazenamento em bloco pela rede para um novo disco, leva tempo no processo. Esse novo disco é então montado no nó pronto para recuperação/importação no disco original conectado ao nó/servidor.

Quando você compara isso com a importação de um [!UICONTROL Database Dump] local, os dados já podem ser recuperados no nó/servidor, portanto, economiza-se muito tempo, pois é necessário apenas um [!UICONTROL Database Import].

## Cenário 2: restaurar um instantâneo

Leia: [Restaurar um instantâneo do Adobe Commerce na infraestrutura de nuvem](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) na documentação do desenvolvedor.

>[!NOTE]
>
>Criar um instantâneo deve ser o primeiro passo após acessar a conta do Adobe Commerce na infraestrutura em nuvem e antes de aplicar grandes alterações. É uma prática recomendada e altamente recomendada.

Leia: [Crie um instantâneo](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) em nossa documentação de desenvolvedor.

## Cenário 3: nenhum instantâneo, build estável (conexão SSH disponível)

Esta seção mostra como redefinir um ambiente quando você não tiver criado um instantâneo, mas puder acessar o ambiente via SSH.

As etapas são:

1. Desative o gerenciamento de configurações.
1. Desinstale o software Adobe Commerce.
1. Reinicializa a ramificação [!DNL git].

Depois de executar essas etapas:

* Sua instalação do Adobe Commerce retorna ao estado Vanilla (banco de dados restaurado; configuração de implantação removida; diretórios em `var` limpos).
* Sua ramificação [!DNL git] foi redefinida para o estado desejado no passado.

Leia as etapas detalhadas abaixo.

### Etapa 0 (Pré-requisito): Remova o config.php para desativar o Gerenciamento de Configuração

Precisamos desabilitar o Gerenciamento de Configurações para que ele não aplique automaticamente as definições de configuração anteriores durante a implantação.

Para desabilitar o Gerenciamento de Configurações, verifique se o diretório `/app/etc/` não contém o arquivo `config.php`.

Para remover o arquivo de configuração, siga estas etapas:

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Remover o arquivo de configuração: `rm app/etc/config.php`

Leia mais sobre o Gerenciamento de configuração:

* [Reduza o tempo de inatividade da implantação do Adobe Commerce na infraestrutura em nuvem](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) em nossa base de dados de conhecimento de suporte.
* [Gerenciamento de configurações para configurações de armazenamento](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) em nossa documentação de desenvolvedor.

### Etapa 1: Desinstale o software Adobe Commerce com o comando setup:uninstall


A desinstalação do software Adobe Commerce remove e restaura o banco de dados, remove a configuração de implantação e limpa diretórios em `var`.

Leia: [Desinstale o software Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) na documentação do desenvolvedor.

Para desinstalar o software Adobe Commerce, siga estas etapas:

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Executar `setup:uninstall` : `bin/magento setup:uninstall`
1. Confirme a desinstalação.

A seguinte mensagem é exibida para confirmar uma desinstalação bem-sucedida:

```php
[SUCCESS]: Magento uninstallation complete.
```

Isso significa que revertemos nossa instalação do Adobe Commerce (incluindo o DB) para seu estado autêntico (Vanilla).

### Etapa 2: redefinir a ramificação [!DNL git]

Com a redefinição [!DNL git], revertemos o código para o estado desejado no passado.

1. Clonar o ambiente no ambiente de desenvolvimento local. Você pode copiar o comando no Cloud Console:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Acesse o histórico de confirmações. Use `--reverse` para exibir o histórico na ordem inversa para maior conveniência: `git log --reverse`
1. Selecione o hash de confirmação no qual você esteve em boas condições. Para redefinir o código para seu estado autêntico (Vanilla), localize a primeira confirmação que criou sua ramificação (ambiente).
   ![alt texto](image.png)
1. Aplicar restauração de [!DNL git] rígida: `git reset --h <commit_hash>`
1. Enviar alterações para o servidor: `git push --force <origin> <branch>`

Depois de executar essas etapas, nossa ramificação [!DNL git] é redefinida e todo o log de alterações [!DNL git] é limpo. O último push [!DNL git] aciona a reimplantação para aplicar todas as alterações e reinstalar o Adobe Commerce.

## Cenário 4: nenhum instantâneo; compilação interrompida (sem conexão [!DNL SSH])

Esta seção mostra como redefinir um ambiente quando ele está em um estado crítico: o procedimento de implantação não pode ter êxito na criação de um aplicativo em funcionamento, tornando a conexão [!DNL SSH] indisponível.

Neste cenário, primeiro você deve restaurar o estado de trabalho do aplicativo do Adobe Commerce usando a redefinição do [!DNL git] e depois desinstalar o software do Adobe Commerce (para descartar e restaurar o banco de dados, remover a configuração da implantação etc.). O cenário envolve as mesmas etapas do Cenário 3, mas a ordem das etapas é diferente e há uma etapa adicional - forçar reimplantação. As etapas são:

1. [Reinicializa a ramificação  [!DNL git] .](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Desative o gerenciamento de configurações.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Desinstale o software Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Forçar reimplantação.

Depois de executar essas etapas, você terá os mesmos resultados do Cenário 3.

### Etapa 4: Forçar reimplantação

Faça uma confirmação (pode ser uma confirmação vazia, embora não recomendemos) e envie-a para o servidor para acionar a reimplantação:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Se a configuração:desinstalação falhar, redefina o banco de dados manualmente

Se a execução do comando `setup:uninstall` falhar com um erro e não puder ser concluída, poderemos limpar o banco de dados manualmente com estas etapas:

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Conecte-se ao banco de dados MySQL: `mysql -h database.internal` (Para ambientes Pro, consulte: [Configurar serviço MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Remover o BD `main`: `drop database main;`
1. Criar um BD `main` vazio: `create database main;`
1. Exclua os seguintes arquivos de configuração: `config.php`, `config.php.bak`, `env.php`, `env.php.bak`

Depois de redefinir o BD, [faça um push [!DNL git] no ambiente para acionar a reimplantação](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) e instale o Adobe Commerce em um BD recém-criado. Ou [execute o comando de reimplantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
