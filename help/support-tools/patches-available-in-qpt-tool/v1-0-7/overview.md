---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.0.7

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.7.

O QPT v1.0.7 inclui os seguintes patches:

1. **MDVA-29148**: corrige o problema ao criar um produto por meio de uma chamada de API; o atributo personalizado de produto do tipo `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multisseleção) não usará seu valor padrão se nenhum valor for fornecido na carga.
1. **MDVA-29389**: corrige o problema com o Relatório Avançado em que o trabalho de cronograma `analytics_collect_data` diz: *A porta deve ser configurada dentro do parâmetro de host (como localhost:3306)*.
1. **MDVA-30594**: corrige o problema em que uma ordem com vários endereços não pode ser salva durante o check-out quando o FPT está configurado.
1. **MDVA-30782**: corrige o problema em que o Bloco Dinâmico é exibido independentemente da regra do carrinho.
1. **MDVA-30815**: corrige o problema em que, quando você altera quantos resultados de pesquisa devem ser exibidos na página de resultados da pesquisa.
1. **MDVA-30837**: adiciona opções de configuração para o cálculo de frete grátis para que o usuário possa configurar o Valor Mínimo do Pedido para obter Frete Gratuito com base no Subtotal (ou Total Geral).
1. **MDVA-30945**: corrige o problema em que você recebe uma mensagem de erro fatal ao atualizar os carrinhos `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: corrige o problema em que o status de pedido personalizado foi alterado para *Processando* após a criação de remessa parcial usando WebApi.
1. **MDVA-31007**: corrige o problema em que os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido na área minha conta e no back-end.
1. **MDVA-31021**: corrige o problema em que existem problemas de desempenho em `module-catalog-import-export/Model/Import/Product/Option.php`. Se houver mais de ~100 mil registros na tabela `catalog_product_option`, um novo CSV com um único produto levará menos de 10 segundos para ser validado.
1. **MDVA-31224**: melhora o desempenho da operação de reindexação `catalog_product_price` para produtos agrupados.
1. **MDVA-31282**: corrige o problema em que ocorrem autorizações duplas em [!DNL Paypal PayFlow Pro] no Adobe Commerce. As autorizações duplas também têm o efeito de ignorar [!DNL PayFlow Pro's] filtros de fraude e duplicar as taxas de transação.
1. **MDVA-31343**: corrige o problema com a classe de corpo removida `page-layout-category-full-width` quando uma categoria é agendada.

Use o menu à esquerda para navegar até uma página de patch específica.
