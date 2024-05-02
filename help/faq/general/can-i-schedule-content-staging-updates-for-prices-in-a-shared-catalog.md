---
title: Posso programar atualizações de Armazenamento temporário de conteúdo para preços em um catálogo compartilhado?
description: A Adobe Commerce não oferece a funcionalidade de agendar uma atualização de preço ([Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) para um ou mais produtos em um catálogo compartilhado.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Posso programar atualizações de Armazenamento temporário de conteúdo para preços em um catálogo compartilhado?

A Adobe Commerce não oferece a funcionalidade de agendar uma atualização de preço ([Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) para um ou mais produtos em um catálogo compartilhado.

Isso significa que não é possível agendar essa atualização de preço diretamente do **Definir Preços e Estrutura** do painel de administração do Commerce (não há **Agendar nova atualização** neste menu).

Ainda assim, você pode usar métodos alternativos e programar uma atualização de preço para:

* um grupo de clientes
* o preço base do produto

## Agendar atualização de preço para um grupo de clientes

1. Início [agendamento de uma nova atualização de produto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Role para baixo até **Preço** e clique em **Advanced Pricing**.

   ![advanced_price.png](assets/advanced_pricing.png){width="600"}

1. No **Seção Preço do Grupo de Clientes**, selecione o Grupo de clientes necessário e defina o preço atualizado.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Termine de programar a atualização como de costume.

Nesse fluxo de trabalho, você só pode atualizar o preço de um único produto; a atualização de preço em massa não está disponível.

Lembre-se: os catálogos compartilhados usam os preços do grupo de clientes.

**Documentação relacionada**

* [Agendando uma atualização (Preparo de conteúdo)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) em nosso guia do usuário.
* [Advanced Pricing](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) em nosso guia do usuário.

## Programar atualização de preço para o preço-base

Consulte o artigo relacionado: [Como a alteração do preço base afeta o preço do catálogo compartilhado?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) em nossa base de conhecimento de suporte.
