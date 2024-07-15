---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.6'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.6.
exl-id: 38e9454b-e278-4b14-a861-2af0623db92e
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.0.6

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.6.

O QPT v1.0.6 inclui os seguintes patches:

1. **MDVA-28202**: corrige o problema em que a Navegação em Camadas não filtra corretamente os produtos configuráveis quando o MSI é usado.
1. **MDVA-28300**: corrige o problema em que a solicitação GQL não reflete as alterações de preço das regras de preço do catálogo.
1. **MDVA-28993**: implementa a funcionalidade *Mínimo deve corresponder* e a pesquisa parcial para o mecanismo [!DNL Elasticsearch]. Soluciona problemas com hifens em consultas de pesquisa.
1. **MDVA-29446**: corrige o problema em que o preço do método de envio não aplicável é mostrado como zero durante o check-out.
1. **MDVA-29787**: corrige o problema em que a regra de destino para produtos relacionados não funciona quando *é uma das* condições são usadas para definir os produtos a serem exibidos.
1. **MDVA-30102**: corrige o problema em que o cache [!DNL Redis] cresce rapidamente, pois os caches de layout não têm TTL.
1. **MDVA-30357**: correção do problema com URLs de imagem incorretas são criadas ao gerar um mapa de site pelo cron.
1. **MDVA-30565**: corrige o problema em que *Nenhuma entidade com cartid = 0* erro é exibida para o cliente convidado no check-out da loja se o carrinho de compras persistente estiver habilitado.
1. **MDVA-30599**: corrige o problema em que as cotações de convidado criadas usando a API são marcadas incorretamente como cotações para clientes conectados.
1. **MDVA-30977**: corrige o problema de produtos aleatórios ausentes das categorias após a reindexação.
1. **MDVA-31006**: corrige o problema em que pedidos duplicados são exibidos depois de fazer um pedido usando o pagamento [!DNL Paypal Express].

Use o menu à esquerda para navegar até uma página de patch específica.
