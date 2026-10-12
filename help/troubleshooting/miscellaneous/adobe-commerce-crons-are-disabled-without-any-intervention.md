---
title: Adobe Commerce [!DNL crons] desabilitada sem intervenção
description: Use este artigo para corrigir o problema em que [!DNL crons] são desabilitados sem intervenção.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '192'
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

Atualize [!DNL ECE Tools] para a versão mais recente [2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Leitura relacionada

* [Baixo desempenho, lento e execução demorada [!DNL crons]](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-42802) em nossa base de dados de conhecimento de suporte.
* [[!DNL Cron] as tarefas bloqueiam tarefas de outros grupos](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) em nossa base de dados de conhecimento de suporte.
* [[!DNL Cron] o trabalho está preso no status &quot;em execução&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) em nossa base de dados de conhecimento de suporte.
