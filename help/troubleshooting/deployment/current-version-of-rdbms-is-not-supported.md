---
title: Erro "A versão atual do RDBMS não é compatível" na implantação
description: 'Este artigo fornece uma solução para quando uma implantação falhar e você tiver o seguinte erro no log de implantação: *a versão atual do RDBMS não é suportada*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Erro &quot;A versão atual do RDBMS não é compatível&quot; na implantação

Este artigo fornece uma solução para quando uma implantação falhar e você tiver o seguinte erro no log de implantação: *A versão atual do RDBMS não é compatível*.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problema

Esta mensagem de erro significa que a versão atual do MariaDB não é mais suportada na versão do Adobe Commerce para a qual você está tentando atualizar e o MariaDB deve ser atualizado para uma versão compatível.


<u>Etapas a serem reproduzidas</u>:

Tentativa de implantação.

<u>Resultado esperado</u>:

Implantação bem-sucedida.

<u>Resultado real</u>:

Falha na implantação com mensagem de erro: *A versão atual do RDBMS não é compatível*.

## Causa

Sua versão do MariaDB não é compatível com a versão do Adobe Commerce para a qual você está tentando atualizar.

## Solução

Você deve atualizar o serviço MariaDB para uma versão compatível antes de atualizar o aplicativo.


Para a ramificação de integração no Adobe Commerce na infraestrutura em nuvem Arquitetura do plano Pro (e todas as ramificações na arquitetura Starter), siga [Configurar serviço](https://devdocs.magento.com/cloud/project/services.html) na documentação do desenvolvedor.

Para preparo e produção na arquitetura do plano Adobe Commerce na infraestrutura em nuvem Pro, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar que os serviços sejam atualizados antes de implantar a atualização de versão do Adobe Commerce.


## Leitura relacionada

* [Práticas recomendadas para builds e implantação](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) na documentação do desenvolvedor.
* [Atualização do Adobe Commerce 2.3.5: tabelas compactas para dinâmicas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) em nossa base de conhecimento de suporte.
