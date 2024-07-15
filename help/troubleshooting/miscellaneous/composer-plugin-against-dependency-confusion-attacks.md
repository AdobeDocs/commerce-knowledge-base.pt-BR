---
title: Plug-in do Composer contra ataques de Confusão de dependência
description: Este artigo fornece informações sobre o plug-in compositor lançado para os ataques de Confusão de dependência e recomendações para evitar o erro. O plug-in do Composer foi introduzido junto com a versão 2.4.3 do Adobe Commerce para proteger os comerciantes do Adobe Commerce de ataques de Confusão de dependência.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Plug-in do Composer contra ataques de Confusão de dependência

Este artigo fornece informações sobre o plug-in compositor lançado para os ataques de Confusão de dependência e recomendações para evitar o erro. O plug-in do Composer foi introduzido junto com a versão 2.4.3 do Adobe Commerce para proteger os comerciantes do Adobe Commerce de ataques de Confusão de dependência.

## Produtos e versões afetados

* Adobe Commerce 2.4.3 e versões futuras (todos os métodos de implantação)

## Problema

Um caso potencial de um ataque ativo de Confusão de Dependências é detectado por meio de pelo menos uma das dependências diretas ou indiretas definidas em `composer.json` pelo plug-in compositor `magento/composer-dependency-version-audit-plugin` durante a instalação/atualização do compositor.

<u>Etapas a serem reproduzidas</u>:

Ao instalar/atualizar o composer, o plug-in do composer interromperá o processo se detectar um possível ataque de Confusão de dependência. Nesse caso, a instalação/atualização do compositor falhará com uma mensagem de erro semelhante a:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Causa

Dependency Confusion ataque permite executar remotamente código arbitrário em um servidor, enganando um gerenciador de dependências (por exemplo, PHP&#39;s Composer) para baixar um pacote malicioso de uma fonte pública em vez do pacote original de um repositório privado.

Esse ataque pode até mesmo não ser detectado se um invasor puder manter a funcionalidade do pacote original.

Os invasores podem explorar essa vulnerabilidade se um pacote só estiver disponível por meio de repositórios privados, mas não estiver registrado no público. Em seguida, o invasor carrega um pacote com o mesmo nome no repositório público e lhe dá uma versão mais alta do que a disponível de forma privada. O gerenciador de dependências comparará as versões de pacotes disponíveis de forma privada e pública e escolherá a mais alta no repositório público. O código mal-intencionado baixado pelo gerenciador de dependências será executado com os mesmos privilégios do código do aplicativo.

## Solução

### Recommendations para comerciantes

* Leve a mensagem de erro exibida quando o plug-in interrompe a instalação/atualização do compositor a sério e entre em contato com o desenvolvedor da extensão se você reconhecer o pacote potencialmente comprometido.
* Você ainda pode instalar o Adobe Commerce com a versão segura do pacote do Marketplace ou outro repositório privado confiável.
* Altere a versão do pacote necessária em seu composer.json para a versão exata encontrada no Marketplace para continuar com a instalação/atualização do compositor.

### Expectativas dos desenvolvedores de extensão

* Não há como saber com certeza se o pacote de um plug-in, se de um repositório público, foi comprometido ou não. O plug-in detectará quando uma versão pública de um pacote em packagist.org tiver uma versão mais alta do que a disponível em um repositório privado como o [repo.magento.com](https://repo.magento.com). Recomendamos que os desenvolvedores de extensão evitem essas situações e não publiquem versões mais recentes do que as disponíveis por meio do [repo.magento.com](https://repo.magento.com).
* A Adobe Commerce entende que o processo de revisão do Marketplace pode atrasar a disponibilidade das extensões, mas o processo está lá para manter os comerciantes seguros e ajudar os desenvolvedores de extensões a encontrar erros acidentais que podem ter perdido.
