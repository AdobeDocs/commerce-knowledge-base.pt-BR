---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.0.8

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.0.8.

O QPT v1.0.8 inclui os seguintes patches:

1. **MDVA-28357**: substitui o analisador padrão por um analisador personalizado por um tokenizer de palavra-chave para o campo SKU no índice [!DNL ElasticSearch] para fazer com que as consultas de pesquisa com curinga funcionem com SKUs que contenham um hífen (&quot;-&quot;).
1. **MDVA-29954**: corrige o problema em que os emails *Nova Solicitação de Registro de Empresa* e *Você foi vinculado a uma empresa* são enviados do endereço errado.
1. **MDVA-30112**: corrige o problema em que, se o número de pedidos exceder o valor *tamanho de grupo*, a Adobe Commerce considerará os pedidos com status *pendente* como inconsistências.
1. **MDVA-30963**: corrige o problema em que os resultados da filtragem de produtos são definidos para conter apenas valores especificados para o escopo *Todas as exibições de loja* no Admin, incluir produtos com valores substituídos no nível de exibição de loja.
1. GET **MDVA-31150**: corrige o problema em que os saldos de cartão-presente e de crédito de armazenamento não são retornados pela chamada da API Rest da Fatura, quando a fatura foi lançada pela chamada da API Rest e o pedido foi parcialmente pago por contas de cartão-presente e de crédito de armazenamento.
1. **MDVA-31242**: corrige o problema em que um sinal de moeda incorreto é exibido na grade [!UICONTROL Credit Memo].
1. **MDVA-31295**: corrige o problema em que os pontos de premiação não são calculados quando um pedido parcial é concluído e os itens são tributados.

Use o menu à esquerda para navegar até uma página de patch específica.
