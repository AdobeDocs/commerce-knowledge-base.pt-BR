---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.0.13

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.13.

O QPT v1.0.13 inclui os seguintes patches:

1. **MCP-87**: tempo de indexação aprimorado para produtos de categoria e indexadores de ações para perfis grandes.
1. **MDVA-13203**: corrige o problema em que o erro *violação de restrição de integridade search_tmp_ table* aparece após uma reindexação completa.
1. **MDVA-19391**: corrige o problema em que `analytics_collect_data` está gerando um erro devido a registros de descrição NULL na tabela `catalog_category_entity_text`.
1. **MDVA-20376**: corrige o problema com a *Entidade sem esse tipo com customerId = 1* erro no `exception.log` para clientes conectados após o posicionamento do pedido.
1. **MDVA-22150**: corrige o problema em que os clientes com um produto configurável no carrinho e um cupom aplicado não podem fazer logon se esse produto configurável estiver desabilitado no Administrador.
1. **MDVA-23426**: corrige o problema em que os emails de notificação enviados pelo Adobe Commerce contêm um corpo em branco com conteúdo que está sendo adicionado como anexo.
1. **MDVA-23764**: corrige o erro em `JsFooterPlugin.php` que afeta a exibição de blocos dinâmicos.
1. **MDVA-30858**: corrige o problema com [!DNL PayPal] relatórios de liquidação não disponíveis em **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** Liquidação conforme esperado.
1. **MDVA-32545**: corrige o problema em que as faturas não são enviadas automaticamente ao criar pedidos do Administrador.
1. **MDVA-32714**: corrige o problema em que o preço de grupo de clientes não está funcionando na consulta de produto do GraphQL.
1. **MDVA-33106**: corrige o problema em que as alterações de produto reagendadas são apagadas após a execução do comando cron `run`.

Use o menu à esquerda para navegar até uma página de patch específica.
