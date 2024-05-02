---
title: Monitoramento da folha de fatos para [!DNL Adobe Commerce on cloud pro infrastructure]
description: Este documento fornece informações sobre o monitoramento e as notificações da infraestrutura do Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Monitoramento da folha de fatos para [!DNL Adobe Commerce on cloud pro infrastructure]

Este documento fornece informações sobre o monitoramento e as notificações da infraestrutura do Adobe Commerce.

O monitoramento permite que comerciantes, integradores de sistemas e equipes internas de Adobe solucionem problemas de disponibilidade do local e espaço em disco insuficiente.

## Solução e solução de problemas

As instâncias do Adobe Commerce geralmente contêm código e configurações personalizados. O Adobe não oferece suporte nem resolve problemas com código e configurações personalizados. O Adobe ajuda os comerciantes a solucionar e identificar problemas em nossa base de conhecimento e fornece soluções recomendadas e práticas recomendadas para prevenção e resolução. Incentivamos os comerciantes e parceiros a usar as tabelas abaixo para entender o que é monitorado e quem é responsável pela resolução.

Quando as notificações forem acionadas, a equipe de suporte da Adobe Commerce fará a triagem do problema. Como parte da triagem, são analisados logs de erros e outros recursos. Com base na triagem, os [!DNL Zendesk] tíquetes de suporte são criados para comerciantes ou parceiros (no caso de atualizações personalizadas) ou para equipes internas do Adobe para resolver o problema.

## Adobe Commerce: monitoramento padrão

Os eventos abaixo são monitorados e a equipe do Adobe Commerce toma as etapas necessárias para resolver e comunicar os problemas identificados.

## Monitoramento da disponibilidade do site

| Disponibilidade do site | Descrição |
|------------|------------|
| **Meta de monitoramento** | Para rastrear a disponibilidade do site. |
| **Instrumentado em** | Solteiro [!DNL URL] selecionado para alto [!DNL SLA]. |
| **Descrição** | A disponibilidade do site é determinada com base nos limites configurados em torno da métrica. A notificação de interrupção do site é acionada se a verificação falhar por 10 minutos e não houver nenhuma implantação ativa em andamento. |
| **Destinatário da notificação** | Comerciante/Parceiro e Adobe. |
| **Ação por Adobe** | Responsável pela triagem e correção se o problema estiver na infraestrutura do Adobe Commerce. |
| **Ação do comerciante** | Responsável pela correção do problema se for causado por alterações ou código personalizado introduzido pelo comerciante/parceiro. Para obter a solução de problemas, consulte: [Solução de problemas de site inativo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Monitoramento de espaço em disco

| Monitoramento de espaço em disco | Descrição |
|------------|------------|
| **Meta de monitoramento** | Para rastrear o uso do espaço em disco. |
| **Instrumentado em** | [!DNL MySQL] partições de disco de mídia e disco de disco. |
| **Métrica** | O espaço livre em disco é monitorado a cada minuto no host. O aviso será gerado se restar apenas 5% ou 2 GB de espaço livre. O limite crítico definido no espaço livre restante é de 2% ou 1 GB. |
| **Descrição** | A notificação é enviada com base nos limites configurados para o espaço livre em disco do host. Espaço em disco adicional é automaticamente adicionado uma vez à montagem relevante ([!DNL MySQL] ou mídia) para evitar uma paralisação do site e dar ao comerciante tempo para liberar espaço em disco e/ou para identificar e resolver qualquer código ou registro que cause um aumento rápido do uso do disco. |
| **Destinatário da notificação** | Comerciante/Parceiro e Adobe. |
| **Ação por Adobe** | Aumente automaticamente o tíquete de suporte e espaço em disco adicional é automaticamente adicionado à montagem relevante ([!DNL MySQL] ou mídia) para evitar uma paralisação do site. |
| **Ação do comerciante** | Para receber alertas contínuos de nível de aviso de espaço em disco, consulte: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: alerta de aviso de disco](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: alerta crítico de disco](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
