---
title: .magento.env.yaml alterações não mostradas em env.php após a implantação
description: Este artigo fornece uma solução para o problema em que as alterações no arquivo .magento.env.yaml não são refletidas em app/etc/env.php após a implantação.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml alterações não mostradas em env.php após a implantação

>[!NOTE]
>
>Se você tiver esse problema, atualize para ece-tools 2002.1.5 para corrigi-lo. 2002.1.5 tem funcionalidade para redefinir o opcache em cada implantação para que nunca seja necessário alterar a configuração `opcache.enable_cli=1`. Se você não quiser atualizar, será necessário executar as etapas alternativas conforme descrito abaixo na solução.

Este artigo fornece uma solução para o problema em que as alterações no arquivo `.magento.env.yaml` não são refletidas no `app/etc/env.php` após a implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problema

As alterações feitas no arquivo `.magento.env.yaml` não afetam o `app/etc/env.php` gerado.

<u>Etapas a serem reproduzidas:</u>

Altere qualquer valor em `.magento.env.yaml` e envie por push para o servidor, onde ele deve definir a configuração (e as configurações de implantação) para o ambiente com check-out no momento. Para ver as etapas, consulte [Variáveis de ambiente > Implantar variáveis](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) na documentação do desenvolvedor.

<u>Resultado esperado:</u>

As alterações feitas no arquivo `.magento.env.yaml` afetam o `app/etc/env.php` gerado.

<u>Resultado real:</u>

As alterações não têm efeito nas variáveis `app/etc/env.php` após a implantação.

## Causa

O problema pode ser causado pelo valor incorreto do parâmetro `opcache.enable_cli` no arquivo `php.ini`.

## Solução

1. Verifique se o sistema está configurado de acordo com [Práticas recomendadas de desempenho do Adobe Commerce > Recomendações de software](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/performance-best-practices/software).
1. Verifique se a diretiva `opcache.enable_cli` em `php.ini` está definida como `0` executando: `php -i | grep opcache.enable_cli`
1. Se a saída se parece com `opcache.enable_cli=1` , edite o arquivo `php.ini` no diretório raiz do projeto e altere `opcache.enable_cli=1` para `opcache.enable_cli=0`
1. Reimplante o projeto.

## Leitura relacionada

* [Nuvem para Adobe Commerce > Criar e implantar](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml).
