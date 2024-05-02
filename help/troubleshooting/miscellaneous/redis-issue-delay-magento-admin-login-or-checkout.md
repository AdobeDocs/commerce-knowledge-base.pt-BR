---
title: Redefine o atraso de problemas ao fazer logon ou check-out no Commerce Admin
description: Este artigo fornece uma correção para o problema que ocorria ao fazer logon no administrador do Commerce ou abrir a página de check-out, o que causava atraso ou tempo limite (mais de 30 segundos). O problema ocorre quando o Redis é usado para armazenamento de sessão.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: aa8c32e3524d669daea7bcf8bc63ed9f8ed16ffa
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Redefine o atraso de problemas ao fazer logon ou check-out no Commerce Admin

Este artigo fornece uma correção para o problema que ocorria ao fazer logon no administrador do Commerce ou abrir a página de check-out, o que causava atraso ou tempo limite (mais de 30 segundos). O problema ocorre quando o Redis é usado para armazenamento de sessão.

**Causa:**   [GitHub issue \#12385](https://github.com/magento/magento2/issues/12385).

**Solução:** atualização para o patch mais recente do Adobe Commerce para corrigir esses problemas para todas as versões do Redis e versões específicas do Adobe Commerce.

## Versões e tecnologias afetadas

* Adobe Commerce na infraestrutura em nuvem versões 2.1.11 - 2.1.13 e 2.2.1
* Adobe Commerce no local versões 2.1.11 - 2.1.13 e 2.2.1
* Redis, todas as versões

Se você usar o Adobe Commerce na versão de infraestrutura em nuvem [2.2.0](#h_64593789291526919876198), uma solução alternativa está disponível.

## Problema

Fazer logon no Commerce Admin ou prosseguir para a página de check-out leva mais de 30 segundos.

Isso só ocorre quando as sessões do usuário são armazenadas em Redis.

## Causa

A Adobe Commerce tinha um problema com o mecanismo de bloqueio de sessão que adicionava um tempo limite de 30 segundos a algumas operações quando o Redis era usado para armazenamento de sessão. Para obter detalhes, consulte [GitHub issue \#12385](https://github.com/magento/magento2/issues/12385).

Este problema foi corrigido no Adobe Commerce 2.1.14 e 2.2.2.

## Soluções: patch ou upgrade

### Solução 1: aplique o patch com uma correção

Para receber um patch, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando o patch. No ticket, especifique a versão do Adobe Commerce e o número de referência correspondente para o patch:

* **2.1.11 e posterior:** MDVA-7835
* **2.2.1:** MDVA-8128

O número de referência geral (independente de versão) é MAGETWO-84289.

### Solução 2: atualize para 2.1.14/2.2.2 ou posterior

Se você já considerou atualizar para o Adobe Commerce 2.2.2 ou posterior, pode usar esta oportunidade de atualização para corrigir o problema.

## Solução alternativa: desativar o bloqueio de sessão

Para desativar o bloqueio de sessão, defina `disable_locking` para `1` na seção Configuração Redis do `env.php` arquivo:

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Essa solução não afeta nenhuma outra funcionalidade da Adobe Commerce.

### Reverter a solução alternativa após aplicar o patch

Depois de aplicar o patch com a correção, a solução alternativa não é mais necessária, portanto, você pode revertê-la (definir `disable_locking` para `0`).

## Adobe Commerce na infraestrutura em nuvem 2.2.0: usar ECE-Tools v2002.0.8 ou posterior {#h_64593789291526919876198}

A variável [ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) pacote de script de implantação com as versões 2002.0.3 - 2002.0.7 [aplica](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) a solução alternativa automaticamente, configuração `disable_locking` para `1`. Isso desativa o mecanismo de bloqueio de sessão do Adobe Commerce 2.2.0, no qual o problema original não ocorre.

Se estiver executando o Adobe Commerce na infraestrutura em nuvem 2.2.0, atualize o ECE-Tools para v2002.0.8 ou posterior. Você também pode considerar atualizar sua Adobe Commerce na infraestrutura em nuvem para a versão 2.2.2 ou posterior.
