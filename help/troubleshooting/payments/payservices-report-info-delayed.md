---
title: Dados do relatório de Serviços de Pagamento Atrasados
description: Este artigo explica por que os dados de relatório nos Serviços de pagamento podem estar atrasados.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Dados do relatório de Serviços de Pagamento Atrasados

Este artigo explica por que os dados de relatório nos Serviços de pagamento podem estar atrasados.

## Produtos e versões afetados

* [Os Serviços de Pagamento](https://marketplace.magento.com/magento-payment-services.html) agora são compatíveis com as versões 2.4.0 a 2.4.4 do Adobe Commerce.

## Problema

Os dados de relatório dos Serviços de pagamento, para os relatórios de status de pagamento de Pagamento e Ordem, podem não ser sincronizados imediatamente.

Depois de faturar (capturar) um pedido ou emitir um aviso de crédito para um pedido, por exemplo, o status do pedido pode não estar imediatamente disponível.

<u>Etapas a serem reproduzidas</u>:

Pré-requisitos: um pedido é feito usando a funcionalidade Serviços de pagamento.

1. Um pedido é [faturado](https://docs.magento.com/user-guide/sales/invoice-create.html) (ou [cancelado](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) ou [reembolsado via memorando de crédito](https://docs.magento.com/user-guide/sales/credit-memos.html)) no [Administrador](https://docs.magento.com/user-guide/stores/admin.html).
1. Navegue até o relatório de status de pagamento da Ordem para ver informações sobre essa ordem.
1. O status é mostrado como `AUTHORIZED`, que é o status do pedido anterior ao faturamento ou outra ação do pedido.

   O Commerce não sincronizou dados e os enviou para Payment Services, portanto, o novo status do pedido ainda não foi reconhecido pelo relatório.

>[!NOTE]
>
>Este é apenas um caso de uso comum. Pode haver outros casos de uso quando uma [ação de pedido](https://docs.magento.com/user-guide/sales/order-actions.html) ocorrer e os dados não estiverem imediatamente disponíveis no relatório aplicável.

<u>Resultado esperado</u>:
Os dados do relatório são preenchidos imediatamente após uma ação em um pedido.

<u>Resultado real</u>:
Pode haver um atraso nos dados visíveis do relatório para ações de pedido recém-concluídas. Os relatórios de pagamento podem incorrer em um atraso de 24 a 48 horas. Os relatórios de status do pagamento de pedidos podem incorrer em um atraso de algumas horas.

## Causa

Há dois fatores que afetam esse atraso nos dados visíveis no Administrador:

* Com que frequência você opta por sincronizar (exportar e manter) dados do Commerce, por meio da [configuração no Administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Período no qual o PayPal publica dados de relatórios.

## Solução

Para relatórios de status de pagamento de Ordem:

1. Navegue até **Vendas** > **Serviços de Pagamento**.
1. Clique em **Status do pagamento da ordem** para exibir a tabela de relatórios de status do pagamento da ordem.
1. Force a ressincronização clicando no ícone **force resync** no canto superior direito da tabela de relatórios.
1. Você deve ver a última alteração de carimbo de data e hora atualizada e novas transações carregadas na tabela de relatórios.

Para os relatórios de pagamento do PayPal, o resultado esperado é um atraso de 24 a 48 horas devido à dependência do período de publicação de dados do PayPal.
