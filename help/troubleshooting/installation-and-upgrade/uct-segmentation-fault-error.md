---
title: Solução de problemas de erros da ferramenta de compatibilidade de atualização
description: Este artigo explica os erros que você pode enfrentar ao usar a Ferramenta de compatibilidade de atualização e fornece soluções para corrigir esses erros para que você possa executar a ferramenta com êxito.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Solução de problemas de erros da ferramenta de compatibilidade de atualização

Este artigo explica os erros que você pode enfrentar ao usar a Ferramenta de compatibilidade de atualização e fornece soluções para corrigir esses erros para que você possa executar a ferramenta com êxito.

## Produtos e versões afetados

* A [Ferramenta de Compatibilidade de Atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=pt-BR) é compatível com as versões do Adobe Commerce a partir da versão 2.3.0.

## Erro de falha de segmentação

<u>Causa</u>:

Quando dois módulos têm o mesmo nome, a Ferramenta de compatibilidade de atualização mostra um erro de falha de segmentação.

<u>Solução</u>:

Para evitar esse erro, é recomendável especificar o caminho para o módulo como um argumento:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> A Ferramenta de compatibilidade de atualização pode não conseguir analisar a base de código se ela contiver dependência circular entre métodos.

## Saída vazia

<u>Etapas a serem reproduzidas</u>:

1. Se, após a execução deste comando:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. A única saída é `Upgrade compatibility tool`:

   ```bash
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Causa</u>:

A causa provável é uma limitação de memória do PHP.

Existem duas soluções possíveis para evitar esta limitação de memória PHP.

<u>Solução 1</u>:

Substitua a limitação de memória definindo `memory_limit` como `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> O `M2_VERSION` é a versão de destino do Adobe Commerce que você deseja comparar à sua instância do Adobe Commerce.

<u>Solução 2</u>:

Adicionar a opção `-m` permite que a Ferramenta de Compatibilidade de Atualização analise cada módulo específico de maneira independente para evitar encontrar dois módulos com o mesmo nome na instância do Adobe Commerce.

Essa opção de comando também permite que a Ferramenta de compatibilidade de atualização analise uma pasta que contém vários módulos:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Consulte a página [Executar a ferramenta em uma interface de linha de comando](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html?lang=pt-BR) para obter mais informações sobre opções de interface de linha de comando.
