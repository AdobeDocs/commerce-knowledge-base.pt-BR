---
title: '"Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.24'''
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.24.
exl-id: 7c296124-c9ae-4b7c-b711-fc39741cabe2
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.24 visão geral

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.24.

O QPT v1.1.24 inclui os seguintes patches:

1. **ACSD-45168**: corrige o problema em que URLs amigáveis para SEO não são geradas para produtos que têm *url_key* atributos substituídos no nível da exibição de armazenamento.
1. **ACSD-46617**: corrige o problema em que a variável **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o valor configurado *Valor Mínimo do Pedido*.
1. **ACSD-46770**: corrige o problema em que emails de pedido de administrador são enviados mesmo quando a variável *Confirmação de pedido por email* está desmarcada.
1. **ACSD-46865**: corrige o problema em que a variável [!UICONTROL Shipment and Credit Memo] a grade não é preenchida quando a indexação assíncrona está habilitada.
1. **ACSD-47004**: corrige o problema em que o IVA não é aplicado a um endereço de faturamento sem uma ID de IVA.
1. **ACSD-47079**: corrige o problema em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado por meio do POST REST API /rest/V1/inventory/source-items.
1. **ACSD-47137**: melhora a velocidade de carregamento da galeria de imagens quando a pasta pub/media é muito grande.
1. **ACSD-47336**: Correções *Algo deu errado.* erro ao dispensar notificações no Administrador do Commerce.
1. **ACSD-47559**: corrige o problema em que a área Visualizar modelo de email não está totalmente visível.
1. **ACSD-47803**: corrige o problema em que as amostras de produtos configuráveis sem estoque são exibidas como disponíveis.
1. **ACSD-47920**: corrige o problema em que os pedidos podem ser feitos por meio da API Rest como um usuário convidado mesmo quando a variável *Permitir check-out de convidado* está desativado.
1. **ACSD-47955**: corrige o problema em que o GraphQL não exibe o desconto do carrinho corretamente.

Use o menu à esquerda para navegar até uma página de patch específica.
