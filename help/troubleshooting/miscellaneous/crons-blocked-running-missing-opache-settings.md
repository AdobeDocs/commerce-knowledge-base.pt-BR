---
title: O Cron para devido a configurações [!DNL OpCache]  desdefinidas ou ausentes
description: Este artigo fornece uma solução para quando os crons param de funcionar devido a configurações  [!DNL OpCache]  incorretas ou ausentes.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron interrompido devido a configurações de [!DNL OpCache] incorretas ou ausentes

Este artigo fornece uma solução para quando o cron para de funcionar devido a configurações [!DNL OpCache] ausentes ou mal definidas.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

O cron parou de funcionar.

## Causa

O módulo [!DNL OpCache] foi atualizado para uma versão mais recente que introduziu um plug-in [!DNL GraphQL] que reescreve o `env.php` em tempo de execução e pode substituir a configuração cron, o que pode ter causado o problema. A configuração [!DNL OpCache] precisa ser atualizada para evitar problemas com o `env.php file`, e isso foi resolvido na [versão 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) do pacote [!DNL ECE Tools].

## Solução

Opção 1: execute o seguinte na ferramenta de linha de comando:

```bash
bin/magento cron:run
```

Talvez seja exibida uma mensagem informando que o cron está desativado.

Opção 2: Abrir o arquivo `app/etc/env.php` - se você vir o arquivo abaixo, o cron foi desabilitado manualmente, não foi habilitado novamente devido a uma falha na implantação ou o problema estava relacionado às configurações de [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Se o cron estiver desabilitado, execute este comando para habilitar novamente o cron: `vendor/bin/ece-tools cron:enable`
1. Verifique se você está na versão mais recente do [!DNL ECE Tools]. Caso contrário, atualize (ou pule para o item 3). Para verificar sua versão existente, execute este comando:
   `composer show magento/ece-tools`
1. Se você já estiver na versão mais recente do [!DNL ECE Tools], verifique a presença do arquivo `op-exclude.txt`. Para fazer isso, execute este comando:
   `ls op-exclude.txt`.
Se esse arquivo não estiver presente, adicione https://github.com/magento/magento-cloud/blob/master/op-exclude.txt ao repositório, confirme a alteração e implante novamente.
1. Sem precisar atualizar o [!DNL ECE Tools], você também pode apenas adicionar/modificar o https://github.com/magento/magento-cloud/blob/master/op-exclude.txt no repositório, confirmar a alteração e reimplantar.

## Leitura relacionada

* [Problemas de verificação de preparação do Cron](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Propriedade Crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [A tarefa do Cron está paralisada no status &quot;em execução&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
