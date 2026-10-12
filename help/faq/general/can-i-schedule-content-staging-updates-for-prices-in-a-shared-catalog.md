---
title: Posso programar atualizações de Armazenamento temporário de conteúdo para preços em um catálogo compartilhado?
description: A Adobe Commerce não oferece a funcionalidade de agendar uma atualização de preço ([Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) para um ou mais produtos em um catálogo compartilhado.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%
---
# Posso programar atualizações de Armazenamento temporário de conteúdo para preços em um catálogo compartilhado?

A Adobe Commerce não oferece a funcionalidade de agendar uma atualização de preço ([Preparo de Conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) para um ou mais produtos em um catálogo compartilhado.

Isso significa que você não pode agendar essa atualização de preço diretamente no menu **Definir Preço e Estrutura** do painel de administração do Commerce (não há nenhum botão **Agendar nova atualização** nesse menu).

Ainda assim, você pode usar métodos alternativos e programar uma atualização de preço para:

* um grupo de clientes
* o preço base do produto

## Agendar atualização de preço para um grupo de clientes

1. Iniciar [agendando uma nova atualização de produto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Role para baixo até o campo **Preço** e clique em **Preços avançados**.

   ![advanced_price.png](assets/advanced_pricing.png){width="600"}

1. Na **seção Preço do Grupo de Clientes**, selecione o Grupo de Clientes necessário e defina o preço atualizado.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Termine de programar a atualização como de costume.

Nesse fluxo de trabalho, você só pode atualizar o preço de um único produto; a atualização de preço em massa não está disponível.

Lembre-se: os catálogos compartilhados usam os preços do grupo de clientes.

**Documentação relacionada**

* [Agendando uma atualização (Preparo de Conteúdo)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) em nosso guia do usuário.
* [Preços avançados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) em nosso guia do usuário.

## Programar atualização de preço para o preço-base

Consulte o artigo relacionado: [Como a alteração do preço base afeta o preço do catálogo compartilhado?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) em nossa base de conhecimento de suporte.
