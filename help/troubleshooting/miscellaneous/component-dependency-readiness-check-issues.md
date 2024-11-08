---
title: Problemas de verificação de preparação de dependência do componente
description: Este artigo fornece soluções para conflitos de dependência de componentes.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Problemas de verificação de preparação de dependência do componente

Este artigo fornece soluções para conflitos de dependência de componentes.

## Resolver conflitos de dependência de componente {#resolve-component-dependency-conflicts}

Sugerimos que você experimente as seguintes soluções na ordem mostrada:

1. [Dependências conflitantes](#trouble-depend-conflict)
1. [Problemas de permissões do sistema de arquivos](#trouble-depend-permission)
1. [O status da Verificação de dependência do componente nunca muda](#trouble-depend-state)

### Dependências conflitantes {#trouble-depend-conflict}

A mensagem *Encontramos dependências de componente conflitantes* é exibida se o Composer não puder determinar quais componentes instalar ou atualizar. Para resolver problemas de dependência de componentes, você deve ser uma pessoa técnica que entende completamente como o Composer funciona.

Veja a seguir um exemplo de mensagem de falha:

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>A mensagem que você vê provavelmente será diferente.

Consulte [Dependências de componentes conflitantes para uma solução](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) em nossa base de dados de conhecimento de suporte.

## Problemas de permissões do sistema de arquivos {#trouble-depend-permission}

Se o proprietário do sistema de arquivos Adobe Commerce não tiver permissões para gravar em diretórios no sistema de arquivos Adobe Commerce, uma mensagem semelhante à seguinte será exibida:

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Defina as permissões do sistema de arquivos conforme discutido no artigo [Visão geral de propriedade e permissões](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) em nossa documentação para desenvolvedores.

## O status da Verificação de dependência do componente nunca muda {#trouble-depend-state}

Em alguns casos, o status da Verificação de dependência de componente não muda, mesmo depois de tentar corrigir os problemas. Nesse caso, você pode excluir ou renomear arquivos chamados `<magento_root>/var/.update_cronjob_status` e `<magento_root>/var/.setup_cronjob_status` e tentar executar o Gerenciador de Componentes novamente.

Renomear ou remover esses arquivos força o Gerenciador de componentes a executar as verificações novamente.
