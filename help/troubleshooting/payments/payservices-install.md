---
title: Solução de problemas de instalação dos Serviços de pagamento
description: Este artigo explica os erros que você pode ter ao instalar os Serviços de pagamento e fornece soluções para corrigir esses erros para que você possa concluir a instalação.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Solução de problemas de instalação dos Serviços de pagamento

Este artigo explica os erros que você pode ter ao instalar os Serviços de pagamento e fornece soluções para corrigir esses erros para que você possa concluir a instalação.

## Produtos e versões afetados

* [Os Serviços de Pagamento](https://marketplace.magento.com/magento-payment-services.html) agora são compatíveis com as versões 2.4.0 a 2.4.4 do Adobe Commerce.

## Problema - Chaves do compositor incorretas

Ao instalar a extensão Payment Services, você pode ver uma mensagem de erro informando que usou chaves do Composer incorretas durante a instalação.

<u>Etapas a serem reproduzidas</u>:

1. Tentativa de [instalar Serviços de Pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=pt-BR).
1. Consulte o seguinte erro:

   *Não foi possível encontrar uma versão correspondente do pacote magento/payment-services. Verifique a ortografia do pacote, a restrição de versão e se o pacote está disponível em uma estabilidade que corresponda à estabilidade mínima (estável).*

<u>Resultado esperado</u>:

Você pode seguir estas [instruções de instalação](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=pt-BR) em nossa documentação do desenvolvedor para instalar com êxito os Serviços de Pagamento.

<u>Resultado real</u>:

Durante a instalação, você verá uma mensagem de erro informando que não usou as teclas do Composer corretas durante a instalação.

### Causa

Você usou chaves do Composer incorretas durante a instalação.

### Solução

Verifique se [suas chaves do Composer estão vinculadas à ID de Magento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=pt-BR#incorrect-composer-keys) usada durante o registro dos Serviços de Pagamento.

## Problema - Uso do mesmo espaço de dados em várias instâncias

Execução de uma configuração de vários ambientes com Serviços de pagamento em cada um.

### Solução

A mesma chave de API pode ser usada em várias instâncias, mas cada instância precisa usar seu próprio espaço de dados SaaS.

Ao criar um projeto SaaS, o Commerce gera um ou mais espaços de dados SaaS dependendo da licença da Commerce:

* Adobe Commerce - Um espaço de dados de produção; dois espaços de dados de teste
* Magento Open Source - Um espaço de dados de produção; sem espaços de dados de teste

Siga as instruções em [Chave de API e chave privada do Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=pt-BR#obtain-api-credentials) para configurar com êxito sua extensão de Serviços de Pagamento.

## Problema - Memória insuficiente para o PHP

Ao instalar a extensão Payment Services, você pode ver uma mensagem de erro informando que você não tem memória suficiente para o PHP.

<u>Etapas a serem reproduzidas</u>:

1. Tentativa de [instalar Serviços de Pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=pt-BR).
1. Consulte o seguinte erro ou semelhante:

   *Erro fatal: Tamanho de memória permitido de 2146435072 bytes esgotado (tentativa de alocar 4096 bytes) em phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php na linha 52*

<u>Resultado esperado</u>:

Você pode seguir estas [instruções de instalação](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=pt-BR) em nossa documentação do desenvolvedor para instalar com êxito os Serviços de Pagamento.

<u>Resultado real</u>:

Durante a instalação, você verá uma mensagem de erro dizendo que você não tem memória suficiente para o PHP.

### Causa

O limite do PHP no seu ambiente não está configurado com um limite alto o suficiente.

### Solução

[Aumente o limite de memória do PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=pt-BR#not-enough-memory-for-php) em seu ambiente no `php.ini`.
