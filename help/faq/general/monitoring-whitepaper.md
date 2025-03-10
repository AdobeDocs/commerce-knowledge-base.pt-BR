---
title: Monitorando folha de fatos para  [!DNL Adobe Commerce on cloud pro infrastructure]
description: Este documento fornece informações sobre o monitoramento e as notificações da infraestrutura do Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Monitorando folha de fatos para [!DNL Adobe Commerce on cloud pro infrastructure]

Este documento fornece informações sobre o monitoramento e as notificações da infraestrutura do Adobe Commerce.

A monitoração permite que comerciantes, integradores de sistemas e equipes internas da Adobe solucionem problemas de disponibilidade local e espaço em disco insuficiente.

## Solução e solução de problemas

As instâncias do Adobe Commerce geralmente contêm código e configurações personalizados. A Adobe não oferece suporte nem resolve problemas com código e configurações personalizados. A Adobe ajuda os comerciantes a solucionar e identificar problemas em nossa base de conhecimento e fornece soluções recomendadas e práticas recomendadas para prevenção e resolução. Incentivamos os comerciantes e parceiros a usar as tabelas abaixo para entender o que é monitorado e quem é responsável pela resolução.

Quando as notificações forem acionadas, a equipe de suporte da Adobe Commerce fará a triagem do problema. Como parte da triagem, são analisados logs de erros e outros recursos. Com base na triagem, tíquetes de suporte [!DNL Zendesk] adicionais são criados para comerciantes ou parceiros (no caso de atualizações personalizadas) ou para equipes internas da Adobe para resolver o problema.

## Adobe Commerce: monitoramento padrão

Os eventos abaixo são monitorados e a equipe do Adobe Commerce toma as etapas necessárias para resolver e comunicar os problemas identificados.

## Monitoramento da disponibilidade do site

| Disponibilidade do site | Descrição |
|------------|------------|
| **Meta de monitoramento** | Para rastrear a disponibilidade do site. |
| **Instrumentado em** | Único(a) [!DNL URL] selecionado(a) para alto [!DNL SLA]. |
| **Descrição** | A disponibilidade do site é determinada com base nos limites configurados em torno da métrica. A notificação de interrupção do site é acionada se a verificação falhar por 10 minutos e não houver nenhuma implantação ativa em andamento. |
| **Destinatário da notificação** | Comerciante/Parceiro e Adobe. |
| **Ação da Adobe** | Responsável pela triagem e correção se o problema estiver na infraestrutura do Adobe Commerce. |
| **Ação do comerciante** | Responsável pela correção do problema se for causado por alterações ou código personalizado introduzido pelo comerciante/parceiro. Para obter a solução de problemas, consulte: [Solução de Problemas de Inatividade do Site](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Monitoramento de espaço em disco

| Monitoramento de espaço em disco | Descrição |
|------------|------------|
| **Meta de monitoramento** | Para rastrear o uso do espaço em disco. |
| **Instrumentado em** | [!DNL MySQL] partições de disco e disco de mídia. |
| **Métrica** | O espaço livre em disco é monitorado a cada minuto no host. O aviso será gerado se restar apenas 5% ou 2 GB de espaço livre. O limite crítico definido no espaço livre restante é de 2% ou 1 GB. |
| **Descrição** | A notificação é enviada com base nos limites configurados para o espaço livre em disco do host. O espaço em disco adicional é adicionado automaticamente uma vez à montagem relevante ([!DNL MySQL] ou mídia) para evitar uma interrupção do site e dar ao comerciante tempo para liberar espaço em disco e/ou identificar e resolver qualquer código ou log que cause um aumento rápido do uso do disco. |
| **Destinatário da notificação** | Comerciante/Parceiro e Adobe. |
| **Ação da Adobe** | Aumente automaticamente o tíquete de suporte e espaço em disco adicional é adicionado automaticamente à montagem relevante ([!DNL MySQL] ou mídia) para evitar uma interrupção do site. |
| **Ação do comerciante** | Para receber alertas contínuos de nível de aviso de espaço em disco, consulte: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: alerta de aviso de disco](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert)</li><li>[[!DNL Managed alerts for Adobe Commerce]: alerta crítico de disco](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert) </li></ul> |
