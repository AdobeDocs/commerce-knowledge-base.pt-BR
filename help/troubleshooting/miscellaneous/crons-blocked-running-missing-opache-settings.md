---
title: O Cron para devido a uma configuração incorreta ou ausente [!DNL OpCache] configurações
description: Este artigo fornece uma solução para quando os crons param de funcionar devido a uma configuração incorreta ou ausente [!DNL OpCache] configurações.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron interrompido devido a uma configuração incorreta ou ausente [!DNL OpCache] configurações

Este artigo fornece uma solução para quando o cron para de funcionar devido a uma configuração incorreta ou ausente [!DNL OpCache] configurações.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

O cron parou de funcionar.

## Causa

A variável [!DNL OpCache] O módulo foi atualizado para uma versão mais recente que introduziu um [!DNL GraphQL] plug-in que reescreve a `env.php` em tempo de execução e pode substituir a configuração cron, o que pode ter causado o problema. A variável [!DNL OpCache] configuração precisa ser atualizada para evitar problemas com o `env.php file`, e isso foi resolvido em [versão 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) do [!DNL ECE Tools] pacote.

## Solução

Opção 1: execute o seguinte na ferramenta de linha de comando:

```bash
bin/magento cron:run
```

Talvez seja exibida uma mensagem informando que o cron está desativado.

Opção 2: abrir o `app/etc/env.php` arquivo - se você vir a seguir, o cron foi desabilitado manualmente, não foi reabilitado devido a uma falha na implantação ou o problema estava relacionado ao [!DNL OpCache] configurações.

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Se o cron estiver desativado, execute este comando para reativar o cron: `vendor/bin/ece-tools cron:enable`
1. Verifique se você está na versão mais recente do [!DNL ECE Tools]. Caso contrário, atualize (ou pule para o item 3). Para verificar sua versão existente, execute este comando:
   `composer show magento/ece-tools`
1. Se você já estiver usando a versão mais recente do [!DNL ECE Tools], verifique a presença da `op-exclude.txt` arquivo. Para fazer isso, execute este comando:
   `ls op-exclude.txt`.
Se esse arquivo não estiver presente, adicione https://github.com/magento/magento-cloud/blob/master/op-exclude.txt ao repositório, confirme a alteração e implante novamente.
1. Sem precisar atualizar [!DNL ECE Tools], você também pode apenas adicionar/modificar https://github.com/magento/magento-cloud/blob/master/op-exclude.txt no repositório, confirmar a alteração e reimplantar.

## Leitura relacionada

* [Problemas de verificação de preparação do Cron](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Propriedade Crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [A tarefa do Cron está paralisada no status &quot;em execução&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
