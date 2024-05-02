---
title: '"Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.7'''
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7 visão geral

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.0.7.

O QPT v1.0.7 inclui os seguintes patches:

1. **MDVA-29148**: corrige o problema ao criar um produto por meio de uma chamada de API, o atributo personalizado do produto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multisseleção), o tipo não usará seu valor padrão se nenhum valor tiver sido fornecido na carga.
1. **MDVA-29389**: corrige o problema nos Relatórios avançados em que a variável `analytics_collect_data` cronjob diz: *A porta deve ser configurada no parâmetro de host (como localhost:3306)*.
1. **MDVA-30594**: corrige o problema em que um pedido com vários endereços não podia ser salvo durante o check-out quando o FPT estava configurado.
1. **MDVA-30782**: corrige o problema em que o Bloco dinâmico é exibido independentemente da regra do carrinho.
1. **MDVA-30815**: corrige o problema em que, ao alterar a quantidade de resultados de pesquisa que devem ser exibidos na página de resultados da pesquisa, você pode corrigir.
1. **MDVA-30837**: adiciona opções de configuração para o cálculo de frete grátis para que o usuário possa configurar o Valor mínimo do pedido para obter frete gratuito com base no Subtotal (ou Total geral).
1. **MDVA-30945**: corrige o problema em que você recebe uma mensagem de erro fatal ao atualizar carrinhos `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: corrige o problema em que o status do pedido personalizado foi alterado para *Processando* após a criação da entrega parcial usando a WebApi.
1. **MDVA-31007**: corrige o problema em que os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido na área minha conta e no back-end do.
1. **MDVA-31021**: corrige o problema em que há problemas de desempenho no `module-catalog-import-export/Model/Import/Product/Option.php`. Se houver mais de ~100 k registros em `catalog_product_option` novo CSV com um único produto leva menos de 10 segundos para ser validado.
1. **MDVA-31224**: melhora o desempenho do `catalog_product_price` operação de reindexação para produtos de pacote.
1. **MDVA-31282**: corrige o problema em que ocorrem autorizações duplas no [!DNL Paypal PayFlow Pro] no Adobe Commerce. As autorizações duplas têm igualmente por efeito contornar [!DNL PayFlow Pro's] de fraude e duplicação das taxas de transação.
1. **MDVA-31343**: corrige o problema com a classe de corpo removida `page-layout-category-full-width` quando uma categoria é agendada.

Use o menu à esquerda para navegar até uma página de patch específica.
