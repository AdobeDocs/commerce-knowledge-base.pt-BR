---
title: Erro durante a implantação ao atualizar para a versão que suporta o PHP 8.1
description: Este artigo fornece uma solução para o erro que ocorre durante a implantação quando se atualiza para uma versão que suporta o PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Erro durante a implantação ao atualizar para a versão que suporta o PHP 8.1

Este artigo fornece uma solução para o erro que ocorre durante a implantação quando se atualiza para uma versão que suporta o PHP 8.1.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.4 e posterior

* Extensão ou tecnologia (Fastly, New Relic etc.) versão PHP 8.1

## Problema

O seguinte erro ocorre durante a implantação quando se atualiza para uma versão que suporta o PHP 8.1.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Causa

O PHP 8.1 já inclui suporte a JSON e não requer que a extensão seja instalada separadamente.

## Solução

Remover JSON do **Tempo de execução** > **Extensões** seção em `.magento.app.yaml` e reimplantar.

## Leitura relacionada

[aplicativo PHP](https://devdocs.magento.com/cloud/project/magento-app-php-application.html) na documentação do desenvolvedor.
