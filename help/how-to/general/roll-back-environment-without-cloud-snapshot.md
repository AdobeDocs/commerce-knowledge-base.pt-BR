---
title: Reverter ambiente sem instantâneo da nuvem
description: Este artigo mostra duas soluções para reverter um ambiente sem ter um instantâneo do seu ambiente no Adobe Commerce na infraestrutura em nuvem.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: d7c714cf5b2f9db139440d814af26c12001bb4d9
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 0%

---

# Reverter ambiente sem instantâneo da nuvem

Este artigo mostra duas soluções para reverter um ambiente sem ter um instantâneo do seu ambiente no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Escolha o mais apropriado para seu caso:

* Se você tiver uma compilação estável, mas nenhum instantâneo válido - [Cenário 1: nenhum instantâneo, compilação estável (conexão SSH disponível)](#scen2).
* Se a compilação for interrompida e você não tiver um instantâneo válido - [Cenário 2: nenhum instantâneo; compilação interrompida (sem conexão SSH)](#scen3).

## Cenário 1: nenhum instantâneo, build estável (conexão SSH disponível) {#scen2}

Esta seção mostra como reverter um ambiente quando você não criou um instantâneo, mas pode acessar o ambiente via SSH.

As etapas são:

1. Desative o gerenciamento de configurações.
1. Desinstale o software Adobe Commerce.
1. Redefina a ramificação Git.

Depois de executar essas etapas:

* sua instalação do Adobe Commerce retorna ao estado Vanilla (banco de dados restaurado; configuração de implantação removida; diretórios em `var` limpos)
* sua ramificação git é redefinida para o estado desejado no passado

Leia as etapas detalhadas abaixo:

### Etapa 0 (Pré-requisito): Remova o config.php para desativar o Gerenciamento de Configuração {#disable_config_management}

Precisamos desabilitar o Gerenciamento de Configurações para que ele não aplique automaticamente as definições de configuração anteriores durante a implantação.

Para desabilitar o Gerenciamento de Configuração, verifique se o diretório `/app/etc/` não contém os arquivos `config.php` (para Adobe Commerce 2.4.x) ou `config.local.php` (para Adobe Commerce 2.1.x).

Para remover o arquivo de configuração, siga estas etapas:

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Remova o arquivo de configuração:
   * Para o Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * Para o Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Saiba mais sobre o Gerenciamento de configurações revisando o [Gerenciamento de configurações para configurações de armazenamento](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) em nossa documentação de desenvolvedor.

### Etapa 1: desinstale o software Adobe Commerce com o comando setup:uninstall {#setup-uninstall}


A desinstalação do software Adobe Commerce remove e restaura o banco de dados, remove a configuração de implantação e limpa diretórios em `var`.

Consulte [Desinstalar o software Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) na documentação do desenvolvedor.

Para desinstalar o software Adobe Commerce, siga estas etapas:

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Executar `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Confirme a desinstalação.

A seguinte mensagem é exibida para confirmar uma desinstalação bem-sucedida:

```php
[SUCCESS]: Magento uninstallation complete.
```

Isso significa que revertemos nossa instalação do Adobe Commerce (incluindo o DB) para seu estado autêntico (Vanilla).

### Etapa 2: redefinir a ramificação Git {#reset-git-branch}

Com a redefinição do Git, revertemos o código para o estado desejado no passado.

1. Clonar o ambiente no ambiente de desenvolvimento local. Você pode copiar o comando no Cloud Console:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Acesse o histórico de confirmações. Use `--reverse` para exibir o histórico na ordem inversa para maior comodidade:

   ```git
     git log --reverse
   ```

1. Selecione o hash de confirmação no qual você esteve em boas condições. Para redefinir o código para seu estado autêntico (Vanilla), localize a primeira confirmação que criou sua ramificação (ambiente).    ![Selecionando um hash de confirmação no console Git](assets/select_commit_hash.png)
1. Aplicar redefinição de git rígida:

   ```git
     git reset --h <commit_hash>
   ```

1. Enviar alterações para o servidor:

   ```git
     git push --force <origin> <branch>
   ```

Depois de executar essas etapas, nossa ramificação Git é redefinida e todo o log de alterações do Git é limpo. O último push do Git aciona a reimplantação para aplicar todas as alterações e reinstalar o Adobe Commerce.

## Cenário 2: nenhum instantâneo; build interrompida (sem conexão SSH) {#scen3}

Esta seção mostra como reverter um ambiente quando ele está em um estado crítico: o procedimento de implantação não pode ser bem-sucedido na criação de um aplicativo em funcionamento, tornando a conexão SSH indisponível.

Nesse cenário, primeiro você deve restaurar o estado de trabalho do aplicativo Adobe Commerce usando a redefinição do Git e, em seguida, desinstalar o software Adobe Commerce (para descartar e restaurar o banco de dados, remover a configuração de implantação etc.). O cenário envolve as mesmas etapas do Cenário 1, mas a ordem das etapas é diferente e há uma etapa adicional - forçar reimplantação. As etapas são:

[&#x200B;1. Redefina a ramificação Git.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Desabilitar Gerenciamento de Configuração.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[&#x200B;3. Desinstale o software Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;ponto; Forçar reimplantação.

Depois de executar essas etapas, você terá os mesmos resultados do Cenário 1.

### Etapa 4: Forçar reimplantação

Faça uma confirmação (pode ser uma confirmação vazia, embora não recomendemos) e envie-a para o servidor para acionar a reimplantação:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Se a configuração :uninstall falhar, redefinir o banco de dados manualmente

Se a execução do comando `setup:uninstall` falhar com um erro e não puder ser concluída, poderemos limpar o banco de dados manualmente com estas etapas:

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Conectar ao BD MySQL:

   ```sql
   mysql -h database.internal
   ```

1. Remover o BD `main`:

   ```sql
   drop database main;
   ```

1. Criar um BD `main` vazio:

   ```sql
   create database main;
   ```

1. Exclua os seguintes arquivos de configuração: `config.php`, `config.php` `.bak`, `env.php` e `env.php.bak`.

Depois de redefinir o BD, [faça um push do Git para o ambiente para acionar a reimplantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) e instalar o Adobe Commerce em um BD recém-criado. Ou [execute o comando de reimplantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Restaurar um instantâneo na Nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Criar um instantâneo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Gerenciamento de instantâneos e backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Gerenciar ramificações com o Cloud Console - Exibir logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Falha na implantação do componente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Gerenciar seu projeto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
