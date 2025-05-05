---
title: Redefinir trabalhos cron travados do Adobe Commerce na infraestrutura em nuvem manualmente
description: os trabalhos cron do Adobe Commerce na infraestrutura em nuvem não terminam de ser executados, ficam presos e impedem que outros trabalhos cron sejam executados. Este artigo mostra como redefinir os trabalhos cron travados manualmente.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Redefinir trabalhos cron travados do Adobe Commerce na infraestrutura em nuvem manualmente

os trabalhos cron do Adobe Commerce na infraestrutura em nuvem não terminam de ser executados, ficam presos e impedem que outros trabalhos cron sejam executados. Este artigo mostra como redefinir os trabalhos cron travados manualmente.

Use esse comando com cuidado! Recomendamos ler o artigo [Redefinir trabalhos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=pt-BR) em nossa base de dados de conhecimento de suporte para obter mais detalhes.

## Etapas

>[!INFO]
>
>Em [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=pt-BR#v2002.0.4), é possível redefinir manualmente os trabalhos cron travados usando um comando CLI via acesso SSH.

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=pt-BR).
1. Executar este comando: `./vendor/bin/ece-tools cron:unlock`

## Avisos

* O comando redefine **todos** trabalhos cron, incluindo aqueles em execução no momento; **use-o somente em casos excepcionais**.
* Evite usar esta solução quando os indexadores estiverem em execução.

## Leia na nossa base de conhecimento de suporte:

[Redefinir trabalhos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=pt-BR)
