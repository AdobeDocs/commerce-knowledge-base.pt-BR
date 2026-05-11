---
title: Não é possível ver vários espaços de dados SaaS após configurar as chaves de API do Adobe AI
description: Este artigo fornece uma solução para os problemas em que você só vê um espaço de dados SaaS depois de configurar as chaves de API para o Adobe AI.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 61f5a526a0c36c91739103c0802bc9794a425f38
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Não é possível ver vários espaços de dados SaaS após configurar as chaves de API do Adobe AI

Depois de configurar as chaves de API para um serviço da Commerce, como os serviços da Adobe AI (Product Recommendations ou Live Search) ou os Serviços de pagamento para o Adobe Commerce, você espera ver vários espaços de dados SaaS no Commerce Services Connector. Dependendo do direito do produto e do tipo de implantação, o conector exibe apenas um espaço de dados SaaS, que é o comportamento esperado.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação): todas as versões
* Magento Open Source: todas as versões
* Extensão ou tecnologia (Fastly, New Relic etc.), Adobe AI (Product Recommendations/Live Search)

## Problema

Depois de configurar as chaves de API do Adobe AI, o sistema mostra apenas um espaço de dados SaaS.

## Causa

O número de espaços de dados SaaS disponíveis depende do direito do produto vinculado à conta do Commerce e do tipo de serviço que está sendo usado.

## Solução

Em geral, o número de espaços de dados SaaS disponíveis depende da licença do Commerce:

* Adobe Commerce: um espaço de dados de produção e dois de teste
* Magento Open Source: um espaço de dados de produção e nenhum espaço de dados de teste

Para Serviços de pagamento, o comportamento padrão é:

* Os Serviços de Pagamento na Adobe Commerce (*Cloud ou no local*) têm três espaços de dados por padrão:
* um espaço de dados de produção
* dois espaços de dados de teste
* Por padrão, os Serviços de pagamento no Magento Open Source têm um espaço de dados

Os clientes que possuem vários projetos na Nuvem ou instalações locais (*live/production*) também podem solicitar espaços de dados adicionais de produção e teste para cada projeto ou instância enviando uma solicitação de Suporte.

Os clientes do Magento Open Source que usam os Serviços de pagamento da Adobe também podem solicitar um espaço de dados adicional. Entre em contato com a equipe de Pagamentos para obter aprovação prévia antes de enviar uma solicitação de Suporte para adicionar um espaço de dados de teste.

>[!NOTE]
> * Não use o mesmo espaço de dados SaaS em vários ambientes ao mesmo tempo. Se um espaço de dados de produção ou teste for reutilizado em ambientes, os dados poderão se tornar mistos e exigir limpeza.
> * Os Serviços de Pagamento na Adobe Commerce (*Cloud/No Local*) têm três espaços de dados por padrão.
> * Por padrão, os Serviços de pagamento do Magento Open Source têm um espaço de dados.
> Para solicitar espaços de dados adicionais:
> * Os clientes do Magento Open Source que usam os Serviços de pagamento da Adobe podem solicitar um espaço de dados adicional. Entre em contato com a equipe de Pagamentos para obter aprovação prévia antes de enviar uma solicitação de Suporte para obter um espaço de dados de teste.
> * Os clientes que possuem vários projetos na Nuvem ou instalações locais (*live/production*) também podem solicitar espaços de dados adicionais de produção e teste para cada projeto ou instância enviando uma solicitação de Suporte.

## Leitura relacionada

[Provisionamento de espaço de dados SaaS](https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
