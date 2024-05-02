---
title: '"Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.37'''
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4ccdba38-8171-4cc4-b8ef-d2c53dec0b47
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.37

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis em [!DNL Quality Patches Tool] (QPT) v1.1.37.

O QPT v1.1.37 inclui os seguintes patches:

1. **ACSD-52613**: corrige o problema em que caches e índices são atualizados mesmo quando não são feitas atualizações no `Inventory_source` por API rest.
1. **ACSD-51884**: corrige o problema em que o caminho do cache de imagem do produto se torna incorreto após a execução do comando resize.
1. **ACSD-53628**: corrige o problema em que o relatório de ordem de venda CSV mostra caracteres especiais incorretos.
1. **ACSD-49843**: corrige o problema em que o link no download do produto não está disponível depois que o item solicitado é faturado automaticamente pelo método de pagamento online com o *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* configuração ativada.
1. **ACSD-53148**: corrige o problema em que duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultavam em dois itens separados no carrinho com o mesmo SKU de produto.
1. **ACSD-47054**: corrige o problema em que a pré-visualização de reindexação executa a reindexação para todos os armazenamentos, causando lentidão.
1. **ACSD-52606**: corrige o problema em que a mensagem de erro *Seu pedido não está pronto para retirada* é exibido quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: corrige o problema em que a imagem não é atualizada no front-end depois de substituí-la por outra imagem com o mesmo nome.
1. **ACSD-53728**: corrige o problema em que o indexador EAV do produto está demorando mais para ser concluído.
1. **ACSD-53979**: corrige o problema de JS que ocorre na página inicial se a mensagem de boas-vindas contiver aspas simples.
1. **ACSD-52143**: corrige o problema em que as opções personalizadas são removidas após a importação do produto.
1. **ACSD-53750**: corrige o *Pipe quebrado ou conexão fechada* erro durante multithread `catalog_product_price` reindexar.

Use o menu à esquerda para navegar até uma página de patch específica.
