---
title: 'Erro de implantação: *erro 7 ao baixar ... porta 443: conexão recusada*'
description: 'Este artigo fornece uma solução para o erro de implantação: *"erro 7 ao baixar ... porta 443: conexão recusada"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Erro de implantação: *erro 7 ao baixar... porta 443: conexão recusada*

Este artigo fornece uma correção para o problema em que a implantação falha com a seguinte mensagem de erro:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Falha na implantação com uma mensagem de erro de **curl 7**.

<u>Etapas a serem reproduzidas</u>:

Acione uma implantação.

<u>Comportamento esperado</u>:

Implantação bem-sucedida.

<u>Comportamento real</u>:

Falha na implantação e o seguinte erro: *erro de curl 7 ao baixar ... porta 443: conexão recusada* aparece no log de implantação.

## Causa

Isso pode ocorrer devido à perda de conexão do cache com o repositório.

## Solução

Peça a um superusuário no projeto para executar este comando:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Para verificar quem é o Superusuário do projeto, consulte [Exibir a função de projeto de um usuário](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) no Guia de Infraestrutura do Commerce na Nuvem.

## Leitura recomendada

* [Solução de problemas de implantação do Adobe Commerce](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [O Adobe Commerce no repositório de nuvem não pôde ser acessado: erro 403 Proibido ou 404 Não encontrado ao implantar](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Falha na implantação com &quot;Erro ao criar projeto: falha no gancho de compilação com código de status 1&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
