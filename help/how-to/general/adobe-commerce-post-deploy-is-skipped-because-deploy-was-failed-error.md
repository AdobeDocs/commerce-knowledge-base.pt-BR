---
title: Adobe Commerce *a pós-implantação é ignorada porque a implantação falhou* erro
description: 'Este artigo explica como investigar um erro de implantação: *A pós-implantação é ignorada porque a implantação falhou*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
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
