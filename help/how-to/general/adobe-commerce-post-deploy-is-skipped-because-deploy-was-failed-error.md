---
title: Adobe Commerce *a pós-implantação é ignorada porque a implantação falhou* erro
description: 'Este artigo explica como investigar um erro de implantação: *A pós-implantação é ignorada porque a implantação falhou*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%
---
# A pós-implantação do Adobe Commerce *foi ignorada porque a implantação falhou* erro

Este artigo explica como investigar um erro de implantação: *A pós-implantação é ignorada porque houve falha na implantação*, o que ocorre durante a implantação em diferentes ambientes, por exemplo, atualização.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem [todas as versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

A implantação falha e retorna uma mensagem de erro genérica, portanto, não está claro como resolver o erro.

## Causa

Indeterminado - a causa dessa mensagem de erro depende do código e do banco de dados implantados.

## Como investigar o erro de implantação

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Para obter o rastreamento de erros para determinar a causa real, SSH conecte o servidor e verifique o arquivo de log `var/log/install_upgrade.log`.
