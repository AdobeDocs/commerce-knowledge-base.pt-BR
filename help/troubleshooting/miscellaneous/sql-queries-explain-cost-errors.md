---
title: "Consultas SQL: EXPLICAR erros de custo"
description: Este artigo fornece soluções para erros de custo EXPLICAR ao executar consultas SQL malsucedidas. O PostgreSQL usa algo chamado [o comando EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) para determinar o custo de consultas SQL. Criamos o Report Builder SQL para também usar esse comando, o que significa que, se o custo for considerado muito alto - a quantidade de recursos necessários para executar o query excede nossos limites - o query não será executado e uma mensagem EXPLAIN será exibida.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Consultas SQL: EXPLICAR erros de custo

Este artigo fornece soluções para erros de custo EXPLICAR ao executar consultas SQL malsucedidas. O PostgreSQL usa algo chamado [o comando EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) para determinar o custo de consultas SQL. Criamos o Report Builder SQL para também usar esse comando, o que significa que, se o custo for considerado muito alto - a quantidade de recursos necessários para executar o query excede nossos limites - o query não será executado e uma mensagem EXPLAIN será exibida.

Há algumas razões pelas quais isso pode acontecer. Estas são as mensagens que você pode receber, o que elas significam e como solucioná-las.

## Não é possível executar a consulta. O valor de custo EXPLICAR de \[xxx\] é muito alto para executar esta consulta.

Se você vir essa mensagem, significa que a execução do query foi considerada muito cara. Temos duas recomendações para essa situação: uma é eliminar qualquer cláusula ORDER BY de seu query, já que são operações caras. A segunda é seguir as dicas em nosso [artigo de otimização](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html) para ajustar sua consulta.

## Não é possível executar a consulta. Essa consulta retorna \[xxx\] linhas, o que excede nosso limite de 10.000

Nesse caso, o número possível de resultados excede o máximo definido para o Report Builder SQL. Há algumas maneiras de reduzir o número de resultados:

* Tente adicionar alguns filtros ao query.
* Use LIMITE, se possível. Algumas tabelas têm um grande número de linhas. A limitação dos resultados pode mantê-lo abaixo do limite de linhas.

## Não é possível analisar a resposta EXPLICAR.

Ops. Essa mensagem geralmente significa que algo provavelmente deu errado da nossa parte. Se continuar recebendo esse erro, entre em contato com o suporte.
