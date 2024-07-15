---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.42

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.42.

O QPT v1.1.42 inclui os seguintes patches:

1. **ACSD-53658**: corrige o problema em que os dados do produto *[!UICONTROL Recently Viewed]* não são atualizados corretamente na exibição da loja.
1. **ACSD-54626**: corrige o problema em que você não pode criar uma nova regra de ordem de compra (`createPurchaseOrderApprovalRule`) com o atributo `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845**: corrige o problema de tempo limite de conexão do MySQL quando `consumer max_messages` = 0.
1. **ACSD-54890**: corrige o problema em que `aggregate_sales_report_bestsellers_data` causa erros de MySQL devido à falta de espaço no disco `/tmp`.
1. **ACSD-55112**: corrige o problema em que o botão *[!UICONTROL Submit review]* pode ser clicado várias vezes sem validação de [!DNL Google reCAPTCHA v3].
1. **ACSD-54264**: corrige o problema em que a mensagem de erro *Você não pode atualizar o atributo solicitado. A ID da linha: store_id* aparece quando um cliente tenta fazer check-out com uma cotação negociável de outra exibição de loja.
1. **ACSD-54418**: corrige o problema em que uma quantidade fixa de desconto é aplicada incorretamente a cada produto filho do pacote com preço dinâmico.
1. **ACSD-55238**: corrige o problema ao salvar a metadescrição de produto vazia.
1. **ACSD-54966**: corrige o problema em que um código de cupom com uso limitado por cliente não pode ser reutilizado se o pedido anterior falhar.
1. **ACSD-54060**: corrige o problema em que um administrador restrito não pode salvar um produto se ele for filho de outro produto atribuído a um escopo diferente.
1. **ACSD-48910**: corrige o problema em que um produto agrupado atribuído a várias origens fica indisponível depois que um pedido é faturado e enviado, mesmo que tenha uma quantidade diferente de zero.
1. **ACSD-55381**: corrige um erro interno do servidor ao consultar campos `configurable_product_option_uid` e `configurable_product_option_value_uid` de um B2B *[!UICONTROL Requisition list]* via GraphQL.
1. **ACSD-55628**: corrige o carregamento de um arquivo no formulário de registro da empresa e substitui um arquivo para um atributo de cliente na loja.

Use o menu à esquerda para navegar até uma página de patch específica.
