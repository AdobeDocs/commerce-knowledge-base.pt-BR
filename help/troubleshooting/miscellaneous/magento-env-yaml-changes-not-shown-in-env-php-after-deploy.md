---
title: .magento.env.yaml alterações não mostradas em env.php após a implantação
description: Este artigo fornece uma solução para o problema em que as alterações no arquivo .magento.env.yaml não são refletidas em app/etc/env.php após a implantação.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml alterações não mostradas em env.php após a implantação

>[!NOTE]
>
>Se você tiver esse problema, atualize para ece-tools 2002.1.5 para corrigi-lo. 2002.1.5 tem a funcionalidade de redefinir o opcache em cada implantação para que nunca seja necessário alterar a configuração `opcache.enable_cli=1`. Se você não quiser atualizar, será necessário executar as etapas alternativas conforme descrito abaixo na solução.

Este artigo fornece uma solução para o problema em que as alterações no `.magento.env.yaml` arquivo não são refletidos na `app/etc/env.php` após a implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as [versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problema

As alterações feitas no `.magento.env.yaml` arquivo não afetam o `app/etc/env.php` gerada.

<u>Etapas a serem reproduzidas:</u>

Alterar qualquer valor em `.magento.env.yaml` e enviar para o servidor, onde deve definir a configuração (e as configurações de implantação) do ambiente com check-out no momento. Para etapas, consulte [Variáveis de ambiente > Implantar variáveis](https://devdocs.magento.com/cloud/env/variables-deploy.html) na documentação do desenvolvedor.

<u>Resultado esperado:</u>

As alterações feitas no `.magento.env.yaml` arquivo afetar o `app/etc/env.php` gerada.

<u>Resultado real:</u>

As alterações não têm efeito sobre a `app/etc/env.php` variáveis após a implantação.

## Causa

O problema pode ser causado pelo valor incorreto do `opcache.enable_cli` parâmetro no `php.ini` arquivo.

## Solução

1. Verifique se o sistema está configurado de acordo com [Práticas recomendadas de desempenho do Adobe Commerce > Recomendações de software](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Verificar se `opcache.enable_cli` diretiva em `php.ini` está definida como `0` executando: `php -i | grep opcache.enable_cli`
1. Se a saída se parecer com `opcache.enable_cli=1` , edite o `php.ini` arquivo no diretório raiz do projeto e altere `opcache.enable_cli=1` para `opcache.enable_cli=0`
1. Reimplante o projeto.

## Leitura relacionada

* [Nuvem para Adobe Commerce > Criar e implantar](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
