---
title: Eu configurei as chaves de API para o Sensei, mas vejo apenas um espaço de dados SaaS
description: Este artigo fornece uma solução para os problemas em que você só vê um espaço de dados SaaS depois de configurar as chaves de API para o Sensei.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Eu configurei as chaves de API para o Sensei, mas vejo apenas um espaço de dados SaaS

Este artigo fornece uma solução para os problemas em que você só vê um espaço de dados SaaS depois de configurar as chaves de API para o Sensei.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação): todas as versões
* Magento Open Source: todas as versões
* Extensão ou tecnologia (Fastly, New Relic etc.), Adobe Sensei (Product Recommendations/Live Search)

## Problema

Eu configurei as chaves de API para o Sensei, mas estou vendo apenas um espaço de dados SaaS.

## Causa

O número de espaços de dados SaaS exibidos depende da sua licença do Commerce:

* Adobe Commerce - Um espaço de dados de produção; dois espaços de dados de teste
* Magento Open Source - Um espaço de dados de produção; sem espaços de dados de teste

## Solução

* Verifique se as chaves de API foram criadas na conta do Proprietário da conta. Mesmo que você tenha recebido acesso compartilhado à conta deles e criado as chaves em sua própria conta, isso não concederá mais de um espaço de dados.
* Se as chaves foram geradas na conta do Proprietário da conta, verifique se a licença está ativa, ou seja, se não há faturas pendentes.
