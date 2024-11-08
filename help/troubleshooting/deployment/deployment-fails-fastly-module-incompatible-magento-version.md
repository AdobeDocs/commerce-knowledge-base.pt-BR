---
title: Falha na implantação do módulo Fastly na versão incompatível do Adobe Commerce
description: "ATUALIZADO: 29 de fevereiro de 2019"
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Falha na implantação do módulo Fastly na versão incompatível do Adobe Commerce

ATUALIZADO: 29 de fevereiro de 2019

Este artigo fornece uma correção para quando a implantação falha porque o módulo Fastly é incompatível com sua versão atual do Adobe Commerce.

**Problema:** Falha na implantação após uma nova confirmação e envio por push, com a seguinte mensagem de erro:

>\[Exceção\] Aviso: argumento ausente 3 para Fastly\\Cdn\\Plugin\\..., chamado em /app/vendor/magento/framework/Interception/Interceptor.php ... e definido em /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Causa:** alterações incompatíveis com versões anteriores no módulo Fastly v1.2.79.

**Solução (temporária):** atualize o módulo Fastly para a versão 1.2.82 ou superior e carregue um novo VCL no Administrador do Commerce. Em seguida, confirme e envie as alterações para acionar uma implantação bem-sucedida.

## Versões afetadas

* Adobe Commerce no local 2.1.X
* Adobe Commerce na infraestrutura em nuvem 2.1.X
* Módulo Fastly 1.2.79

## Problema

Ao confirmar e enviar as alterações para o ambiente de integração, produção ou preparo, geralmente a próxima etapa é acionar o processo de implantação. Isso é feito automaticamente na edição do Adobe Commerce na infraestrutura em nuvem e manualmente no Adobe Commerce no local.

A implantação pode falhar com as seguintes mensagens de erro:

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Se você estiver usando o Adobe Commerce na solução de infraestrutura em nuvem, verá esta mensagem de erro no [log de implantação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations). Para o Adobe Commerce no local, você verá o erro na linha de comando.

## Causa

O problema é causado pelas alterações incompatíveis com versões anteriores no módulo Fastly v1.2.79.

## Solução

Atualize o módulo Fastly para a versão 1.2.82 ou superior.

Para fazer isso, siga estas etapas:

1. Execute um dos seguintes comandos:
   * se o módulo Fastly estiver incluído no magento-cloud-metappackage:    <pre>atualização do composer magento/magento-cloud-metappackage</pre>
   * se o módulo Fastly foi instalado separadamente (por exemplo, caso você esteja usando o Adobe Commerce no local, não o cloud edition) <pre>atualização rápida do composer/magento2</pre>
1. Confirme e envie as alterações e acione o processo de implantação se ele não for feito automaticamente.
1. No Administrador, [carregue o novo VCL para o Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
