---
title: Erro "O aplicativo atualizador não está disponível"
description: Este artigo fala sobre a solução para o problema "O aplicativo atualizador não está disponível" que você pode enfrentar ao tentar atualizar/instalar o Adobe Commerce no local usando o Assistente de configuração da Web.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Erro &quot;O aplicativo atualizador não está disponível&quot;

Este artigo fala sobre a solução para o problema &quot;O aplicativo atualizador não está disponível&quot; que você pode enfrentar ao tentar atualizar/instalar o Adobe Commerce no local usando o Assistente de configuração da Web.

## Problema

A seguinte mensagem é exibida na verificação de preparação:

![Captura de tela_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Produtos/versões afetadas

* Adobe Commerce no local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Solução

Para resolver esse problema, veja se há um diretório `<magento_root>/update` que contenha arquivos e subdiretórios. Caso contrário, consulte [Configurar o atualizador](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error) na documentação do desenvolvedor.
