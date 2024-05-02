---
title: Problemas de verificação de preparação da versão do PHP
description: Este artigo fala sobre as soluções para os problemas de versão do PHP que você pode enfrentar ao instalar/atualizar o Adobe Commerce no local usando o Assistente de configuração da Web.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Problemas de verificação de preparação da versão do PHP

Este artigo fala sobre as soluções para os problemas de versão do PHP que você pode enfrentar ao instalar/atualizar o Adobe Commerce no local usando o Assistente de configuração da Web.

>[!WARNING]
>
>No Adobe Commerce na infraestrutura em nuvem, observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando o upgrade de serviço necessário e informando o horário em que você deseja que o processo de upgrade tenha início.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Versão PHP não suportada

### Problema

A verificação falha porque você está usando uma versão PHP não suportada.

### Solução

Para resolver esse problema, use uma das versões compatíveis listadas em nossa documentação do desenvolvedor [Requisitos do sistema 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) e [Requisitos do sistema 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## A verificação de preparação do PHP não é exibida

### Problema

A verificação de preparação do PHP não exibe a versão do PHP como mostra a figura a seguir.
![up-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Solução

Este é um sintoma de configuração incorreta do trabalho cron. Para obter mais informações, consulte [Configurar trabalhos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) na documentação do desenvolvedor.

## Versão incorreta do PHP

### Problema

A verificação relata a versão incorreta do PHP. Normalmente, isso acontece apenas com usuários avançados que têm várias versões do PHP instaladas. Em alguns casos, a verificação de prontidão falha; em outros casos, ela pode passar.

Se a versão do PHP relatada pela verificação de preparação estiver incorreta, é o resultado de uma incompatibilidade de versões do PHP entre a CLI do PHP e o plug-in do servidor Web. O Adobe Commerce exige que você use *uma versão* do PHP tanto para a CLI (que executa o cron) como para o servidor Web (que executa o Commerce Admin, o Gerenciador de Componentes e a Atualização do Sistema).

### Solução

Nós assumimos que se você tem esse problema, você é um usuário avançado que provavelmente instalou várias versões do PHP em seu sistema.

Para resolver o problema, tente o seguinte:

* Reinicie seu servidor web ou php-fm.
* Verifique a `$PATH` variável de ambiente para múltiplos caminhos para o PHP.
* Use o `which php` comando para localizar o primeiro executável PHP no seu caminho; se ele não estiver correto, remova-o ou crie um link simbólico para a versão correta do PHP.
* Use um [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) para coletar mais informações.
* Certifique-se de executar uma versão do PHP compatível de acordo com nossos requisitos de sistema na documentação do desenvolvedor:
   * [Requisitos de sistema do Adobe Commerce 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Requisitos de sistema do Adobe Commerce 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* Defina as mesmas configurações do PHP para a linha de comando do PHP e para o plug-in do servidor Web PHP conforme discutido em [Opções de configuração do PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) na documentação do desenvolvedor.
