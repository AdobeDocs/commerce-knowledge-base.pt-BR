---
title: Adobe Commerce [!DNL crons] desabilitado sem intervenção
description: Use este artigo para corrigir o problema em que [!DNL crons] são desabilitados sem intervenção.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons desabilitados sem intervenção

Este artigo fornece uma solução para quando [!DNL crons] são desabilitados sem intervenção.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problema

Seus [!DNL crons] estão desabilitados após a implantação.

<u>Etapas a serem reproduzidas</u>:

Implantar.

<u>Resultado esperado</u>:

Seus [!DNL crons] estão em execução.

<u>Resultado real</u>:

Seus [!DNL crons] estão desabilitados após a implantação.

## Causa

Um problema com as configurações de [!DNL OPcache].

## Solução

Atualize [!DNL ECE Tools] para a versão mais recente [2002.1.13](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Leitura relacionada

* [Baixo desempenho, lento e execução demorada [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html?lang=pt-BR) em nossa base de dados de conhecimento de suporte.
* [[!DNL Cron] as tarefas bloqueiam tarefas de outros grupos](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=pt-BR) em nossa base de dados de conhecimento de suporte.
* [[!DNL Cron] o trabalho está preso no status &quot;em execução&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=pt-BR) em nossa base de dados de conhecimento de suporte.
