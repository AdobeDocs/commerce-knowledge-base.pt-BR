---
title: Adobe Commerce [!DNL crons] desabilitado sem intervenção
description: Use este artigo para corrigir o problema em que [!DNL crons] são desativados sem intervenção.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons desabilitados sem intervenção

Este artigo fornece uma solução para quando [!DNL crons] são desativados sem intervenção.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, tudo [versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problema

Seu [!DNL crons] são desativados após a implantação.

<u>Etapas a serem reproduzidas</u>:

Implantar.

<u>Resultado esperado</u>:

Seu [!DNL crons] estão em execução.

<u>Resultado real</u>:

Seu [!DNL crons] são desativados após a implantação.

## Causa

Um problema com o [!DNL OPcache] configurações.

## Solução

Atualizar [!DNL ECE Tools] para a versão mais recente [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Leitura relacionada

* [Baixo desempenho, lento e execução demorada [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) em nossa base de conhecimento de suporte.
* [[!DNL Cron] tarefas bloqueiam tarefas de outros grupos](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) em nossa base de conhecimento de suporte.
* [[!DNL Cron] a tarefa está paralisada no status &quot;em execução&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) em nossa base de conhecimento de suporte.
