---
title: Diagnóstico de discrepâncias de receita de comércio eletrônico do Google
description: '"Este artigo fornece soluções para discrepâncias entre o Google e o Magento Business Intelligence (MBI). O rastreamento de comércio eletrônico do Google ativa a conta do Google Analytics e os painéis do MBI, mas isso faz com que muitos clientes nos perguntem: Ambas as ferramentas devem relatar a mesma quantidade de **pedidos** e **receita**?'''
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Diagnóstico de discrepâncias de receita de comércio eletrônico do Google

Este artigo fornece soluções para discrepâncias entre o Google e o Magento Business Intelligence (MBI). O rastreamento de comércio eletrônico do Google ativa sua conta Google Analytics e seus painéis MBI, mas isso faz com que muitos clientes nos perguntem: As duas ferramentas devem relatar a mesma quantidade de **pedidos** e **receita**?

Em nossa experiência, a resposta é &quot;não&quot; em quase todas as instâncias. Isso ocorre porque o rastreamento de eCommerce do Google obtém as informações do pedido durante um evento de clique de botão no seu site, que perde muitos atributos de pedido registrados posteriormente no banco de dados, desde pedidos que não são registrados até pedidos que são cancelados ou reembolsados posteriormente.

Sabemos que uma discrepância entre o Google e o MBI pode causar incerteza para você e sua equipe. Queremos ajudá-lo a entender a diferença entre esses dois números, que podem revelar ajustes a serem feitos em sua conta ou banco de dados do Google.

## Por que a DG relata **menos** receita que meu banco de dados?

Quando o Google Analytics relata menos os pedidos e a receita, isso indica que não está capturando todos os pedidos que estão sendo feitos no site. Como você sabe que os dados do banco de dados são o número definitivo, você pode seguir algumas etapas para tentar determinar a causa raiz e, possivelmente, ajudar a Google a obter mais informações.

* Nem sempre o rastreamento de comércio eletrônico do Google estava ativado. Tente observar um período menor e mais recente.
* Seu rastreamento de comércio eletrônico do Google não está configurado para capturar compras de determinados navegadores, sistemas operacionais ou dispositivos.
* O evento de clique associado ao rastreamento do eCommerce do Google não está rastreando corretamente o imposto, o frete ou outras taxas acima do total do pedido.
* O carimbo de data e hora do banco de dados está em um fuso horário diferente do carimbo de data e hora dos Google Analytics.
* Pessoas podem visitar seu site por meio de janelas incógnitas ou com cookies desativados.

## Por que a DG relata **mais** receita do que meu banco de dados?

Descobrimos que é mais comum que os Google Analytics relatem pedidos e receita em excesso do que um banco de dados de comércio eletrônico. Isso nem sempre é uma coisa ruim. Seu banco de dados é o registro definitivo de transações feitas em seu site, e há vários motivos pelos quais o Google pode estar relatando valores altos mesmo quando você o configurou perfeitamente:

* O rastreamento de comércio eletrônico está capturando cliques de botão duplicados registrando somente como um único pedido em seu banco de dados.
* Você tem um alto número de pedidos cancelados, reembolsados ou fraudados, que é uma alteração de estado que ocorre depois que o eCommerce rastreia os dados.
* As métricas de **Receita** e **Pedidos** excluem deliberadamente pedidos de teste ou internos, que a Google não consegue diferenciar.
* Os pedidos não são colocados no banco de dados em determinadas circunstâncias.
* O rastreamento de comércio eletrônico do Google não tem conhecimento de cupons e descontos no pedido.
* O carimbo de data e hora do banco de dados está em um fuso horário diferente do carimbo de data e hora dos Google Analytics.

Lembre-se de que, mesmo que o Google esteja relatando um número maior do que o seu banco de dados, provavelmente ainda faltam alguns pedidos pelos motivos detalhados na seção acima.

## Solução de problemas

* Crie um clone da métrica **Receita** sem filtros que restrinjam o resultado. Os filtros Pedidos contados ou Clientes contados são importantes, mas a Google não tem um filtro equivalente.
* Audite um pequeno período recente, como um período de algumas horas no início desta semana.
* Depois de configurar o rastreamento de comércio eletrônico do Google no MBI, use Filtrar ou Agrupar para auditar uma única Source, Medium ou Campanha. Em seguida, faça o mesmo no Google. Uma fonte com menos tráfego/receita será melhor, pois parece ter menos margem para erros.
