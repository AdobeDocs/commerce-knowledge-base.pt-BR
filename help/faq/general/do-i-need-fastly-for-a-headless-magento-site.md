---
title: O Fastly é necessário para um site do Adobe Commerce Headless?
description: O Fastly é necessário para um site do Adobe Commerce Headless?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%
---
# O Fastly é necessário para um site do Adobe Commerce Headless?

>[!NOTE]
>
>Todos os clientes devem usar o Fastly em seus ambientes de produção e preparo. O Fastly é uma Rede de Entrega de Conteúdo (CDN) que fornece armazenamento em cache de página completa, otimização de imagens e serviços de segurança (DDoS e WAF) como parte de seu Adobe Commerce em projetos de infraestrutura em nuvem. Esses são os componentes principais da solução da Adobe Commerce, fornecendo melhor desempenho e segurança. Esses recursos fazem parte da conformidade PCI da Adobe. Você deve configurar esses serviços do Fastly nos ambientes Starter Master, Staging, Pro Staging e Production. Se você estiver usando o Adobe Commerce em uma implantação headless, todo o tráfego da API proveniente da Internet pública deverá passar pelo Fastly e recomendamos que você use o Fastly para armazenar as respostas do GraphQL em cache. Consulte o [Guia do desenvolvedor do GraphQL > Armazenamento em cache com o Fastly](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly) em nossa documentação do desenvolvedor.

## **Pergunta**

Estou desenvolvendo uma implementação headless do Adobe Commerce. Ainda preciso usar o Fastly como um serviço de CDN para ele?

## **Resposta**

Não, você não. Nessa situação, você pode pular o uso do Fastly - pelo menos, no início do desenvolvimento.

A única situação que talvez você não queira ativar é para uma implantação headless.
Consulte [Cloud para Adobe Commerce > Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) em nossa documentação do desenvolvedor.

Ainda assim, provavelmente, você precisará do Fastly para usar seu certificado SSL.

Todos os clientes do Adobe Commerce na infraestrutura em nuvem obtêm um certificado SSL compartilhado da Fastly como parte do plano de assinatura na nuvem. Adicionar o próprio certificado SSL ao Fastly é uma opção paga separada e bastante cara. Portanto, recomendamos ativar o Fastly e, pelo menos, testá-lo nos ambientes de Preparo e Produção antes da ativação, mesmo para o site headless do Adobe Commerce.

## Mais informações

* [Sites headless: qual é o problema com a arquitetura dissociada?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) por [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) em nossa documentação para desenvolvedores.
