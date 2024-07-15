---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.35

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.35.

O QPT v1.1.35 inclui os seguintes patches:

1. **ACSD-51899**: corrige o problema em que o endereço de remessa padrão na etapa de remessa do check-out é preenchido automaticamente com um endereço de retirada na loja selecionado anteriormente.
1. **ACSD-52041**: corrige o problema em que a mensagem de erro: *[ERRO] [!DNL Page Builder] foi renderizada por 5 segundos sem liberar bloqueios*. aparece no navegador [!DNL Chrome] ao salvar o conteúdo editado com [!DNL Page Builder].
1. **ACSD-52095**: corrige o problema em que o valor `manage_stock` era definido incorretamente como 0 no arquivo CSV após a exportação do produto.
1. **ACSD-51358**: corrige o problema em que a remoção de uma atualização agendada sem uma data de término leva à remoção de outras atualizações agendadas para a mesma entidade.
1. **ACSD-48070**: corrige o problema em que a edição de uma atualização agendada aciona uma exceção.
1. **ACSD-51890**: corrige o problema em que o botão [!UICONTROL Submit review] pode ser clicado várias vezes sem a validação do reCAPTCHA v3 [!DNL Google].
1. **ACSD-51984**: corrige o problema em que *Usar valor padrão e valores de campo de produto não padrão* desmarcados não são salvos no segundo modo de exibição de site, loja e loja.
1. **ACSD-52398**: corrige o erro *A quantidade solicitada não está disponível* que ocorre ao tentar atualizar a quantidade de um produto agrupado no carrinho na loja.
1. **ACSD-52786**: corrige o problema em que um SKU de condição de regra de catálogo é aplicado a todos os produtos que começam com o SKU fornecido.
1. **ACSD-52921**: corrige o problema em que ocorre um erro interno ao solicitar detalhes do carrinho à GraphQL quando há um produto configurável indisponível no carrinho.
1. **ACSD-51683**: corrige o problema em que uma opção personalizável não pode ser adicionada ao carrinho usando o GraphQL.
1. **ACSD-52133**: corrige o problema em que uma conta de cliente não pode ser salva após uma atualização.
1. **ACSD-52202**: corrige o problema em que a quantidade vendável do estoque padrão muda incorretamente para 0 quando um estoque não padrão é alterado para 0 na execução de pedidos.
1. **ACSD-51265**: corrige o problema com o desempenho de reindexação do `catalog_product_price` quando há muitos produtos agrupados no sistema.
1. **ACSD-52831**: corrige o problema em que os clientes não podem fazer pedidos de cotação negociáveis quando [!DNL Google reCAPTCHA v3 Invisible] está habilitado.
1. **ACSD-51845**: corrige o problema em que os produtos subsequentes com preços de camada e diferentes conjuntos de atributos não podem ser atualizados por meio da API REST em massa assíncrona.
1. **ACSD-52815**: corrige o problema em que a entrada para o campo de quantidade de uma fonte não padrão suporta apenas até 6 dígitos, ao contrário de 8 para um estoque padrão.
1. **ACSD-51149**: corrige o problema em que [!UICONTROL Scheduled ImportExport] com [!UICONTROL Catalog Permissions] habilitado invalida indexadores e liberações de cache pelo cron.
1. **ACSD-50815**: corrige o problema em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupado.
1. **ACSD-52399**: corrige o problema em que a opção de produto configurável com uma Qtd. vendável de 0 mostra *Em Estoque* na página do produto.

Use o menu à esquerda para navegar até uma página de patch específica.
