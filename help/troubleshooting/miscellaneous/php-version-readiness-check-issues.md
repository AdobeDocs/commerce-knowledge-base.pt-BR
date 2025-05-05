---
title: Problemas de verificação de preparação da versão do PHP
description: Este artigo fala sobre as soluções para os problemas de versão do PHP que você pode enfrentar ao instalar/atualizar o Adobe Commerce no local usando o Assistente de configuração da Web.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Problemas de verificação de preparação da versão do PHP

Este artigo fala sobre as soluções para os problemas de versão do PHP que você pode enfrentar ao instalar/atualizar o Adobe Commerce no local usando o Assistente de configuração da Web.

>[!WARNING]
>
>No Adobe Commerce na infraestrutura em nuvem, observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando a atualização de serviço necessária e informando a hora em que deseja que o processo de atualização tenha início.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Versão PHP não suportada

### Problema

A verificação falha porque você está usando uma versão PHP não suportada.

### Solução

Para resolver esse problema, use uma das versões com suporte listadas em nossa documentação do desenvolvedor [Requisitos do Sistema da versão 2.3.x](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/system-requirements) e [Requisitos do Sistema da versão 2.2.x](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/system-requirements).

## A verificação de preparação do PHP não é exibida

### Problema

A verificação de preparação do PHP não exibe a versão do PHP como mostra a figura a seguir.
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Solução

Este é um sintoma de configuração incorreta do trabalho cron. Para obter mais informações, consulte [Configurar trabalhos cron](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/next-steps/configuration) na documentação do desenvolvedor.

## Versão incorreta do PHP

### Problema

A verificação relata a versão incorreta do PHP. Normalmente, isso acontece apenas com usuários avançados que têm várias versões do PHP instaladas. Em alguns casos, a verificação de prontidão falha; em outros casos, ela pode passar.

Se a versão do PHP relatada pela verificação de preparação estiver incorreta, é o resultado de uma incompatibilidade de versões do PHP entre a CLI do PHP e o plug-in do servidor Web. O Adobe Commerce requer que você use *uma versão* do PHP para a CLI (que executa o cron) e o servidor Web (que executa o Commerce Admin, o Gerenciador de Componentes e a Atualização do Sistema).

### Solução

Nós assumimos que se você tem esse problema, você é um usuário avançado que provavelmente instalou várias versões do PHP em seu sistema.

Para resolver o problema, tente o seguinte:

* Reinicie seu servidor web ou php-fm.
* Verifique a variável de ambiente `$PATH` quanto a múltiplos caminhos para PHP.
* Use o comando `which php` para localizar o primeiro executável PHP no seu caminho; se ele não estiver correto, remova-o ou crie um link simbólico para a versão correta do PHP.
* Use uma página [`phpinfo.php`](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software) para coletar mais informações.
* Certifique-se de executar uma versão do PHP compatível de acordo com nossos requisitos de sistema na documentação do desenvolvedor:
   * [Requisitos de Sistema do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/system-requirements)
* Defina as mesmas configurações do PHP para a linha de comando do PHP e para o plug-in do servidor Web PHP conforme discutido em [Opções de configuração do PHP](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/system-requirements#php-settings) em nossa documentação do desenvolvedor.
