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

Use esse comando com cuidado! Recomendamos a leitura do [Reinicializa os trabalhos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) artigo em nossa base de conhecimento de suporte para obter mais detalhes.

## Etapas

>[!INFO]
>
>De [Ferramentas ECE v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) você pode redefinir manualmente os trabalhos cron travados usando um comando CLI por meio do acesso SSH.

1. [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Execute este comando: `./vendor/bin/ece-tools cron:unlock`

## Avisos

* O comando é redefinido **all** trabalhos cron, incluindo aqueles em execução atualmente; **use-o somente em casos excepcionais**.
* Evite usar esta solução quando os indexadores estiverem em execução.

## Leia na nossa base de conhecimento de suporte:

[Reinicializa os trabalhos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
