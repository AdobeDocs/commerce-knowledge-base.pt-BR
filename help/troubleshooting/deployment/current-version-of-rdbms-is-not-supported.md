---
title: Erro "A versão atual do RDBMS não é compatível" na implantação
description: 'Este artigo fornece uma solução para quando uma implantação falhar e você tiver o seguinte erro no log de implantação: *a versão atual do RDBMS não é suportada*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Erro &quot;A versão atual do RDBMS não é compatível&quot; na implantação

Este artigo fornece uma solução para quando uma implantação falha e você tem o seguinte erro no log de implantação: *não há suporte para a versão atual do RDBMS*.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problema

Esta mensagem de erro significa que a versão atual do MariaDB não é mais suportada na versão do Adobe Commerce para a qual você está tentando atualizar e o MariaDB deve ser atualizado para uma versão compatível.


<u>Etapas a serem reproduzidas</u>:

Tentativa de implantação.

<u>Resultado esperado</u>:

Implantação bem-sucedida.

<u>Resultado real</u>:

Falha na implantação com mensagem de erro: *não há suporte para a versão atual do RDBMS*.

## Causa

Sua versão do MariaDB não é compatível com a versão do Adobe Commerce para a qual você está tentando atualizar.

## Solução

Você deve atualizar o serviço MariaDB para uma versão compatível antes de atualizar o aplicativo.


Para obter a ramificação de integração na arquitetura de plano Pro da infraestrutura em nuvem do Adobe Commerce (e todas as ramificações na arquitetura Starter), siga [Configurar serviço](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) na documentação do desenvolvedor.

Para Preparo e Produção na arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar que os serviços sejam atualizados antes de implantar a atualização da versão do Adobe Commerce.


## Leitura relacionada

* [Práticas recomendadas para compilações e implantação](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) em nossa documentação para desenvolvedores.
* [Atualização do Adobe Commerce 2.3.5: compacte para tabelas dinâmicas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=pt-BR) em nossa base de dados de suporte.
