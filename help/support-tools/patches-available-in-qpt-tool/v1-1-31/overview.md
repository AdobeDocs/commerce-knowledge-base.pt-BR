---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.31

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.31.

O QPT v1.1.31 inclui os seguintes patches:

1. **ACSD-50817**: otimiza o trabalho cron `sales_clean_quotes` para ser executado mais rápido adicionando um índice composto em `store_id` e `updated_at` colunas na tabela de aspas.
1. **ACSD-50345**: corrige o problema em que: [!DNL Google reCAPTCHA v2] não é recarregado após o envio de um pagamento com falha, [!DNL Google reCAPTCHA v3 Invisible] não está trabalhando no check-out e o pedido não pode ser feito e o evento [!UICONTROL PlaceOrder] não foi disparado.
1. **ACSD-49392**: corrige o problema em que o status do pedido muda para fechado após um reembolso parcial para um produto agrupado.
1. **ACSD-51036**: corrige o problema em que as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição das informações de status de remessa na tabela [!UICONTROL Items Ordered].
1. **ACSD-50858**: corrige o problema em que um cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.

Use o menu à esquerda para navegar até uma página de patch específica.
