---
title: Módulo Magento_BundleSampleData desconhecido
description: Este artigo fornece uma correção para o erro de módulo desconhecido durante a instalação do Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Módulo Magento_BundleSampleData desconhecido

Este artigo fornece uma correção para o erro de módulo desconhecido durante a instalação do Adobe Commerce.

## Problema {#details}

Durante a instalação, uma mensagem semelhante à seguinte é exibida:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Solução {#solution}

Tente executar cada um dos procedimentos a seguir de cada vez e tente instalar novamente.

1. Execute o Assistente de configuração da Web. Os módulos estão listados em  **Configurações avançadas de módulos**. Para desativar o **Magento\_BundleSampleData** , limpe a **Magento\_BundleSampleData** como mostra a figura a seguir.

   ![tshoot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Limpar todos os dados e o histórico do navegador da Web.
1. Se você tiver o Chrome, apague todos os dados do navegador relacionados ao seu site.  Ir para **Configurações** > **Opções avançadas** > **Privacidade** > **Configurações de conteúdo** > **Todos os cookies e dados do site**. Na coluna Site, clique no endereço do servidor do Adobe Commerce e clique em **Remover tudo**.
