---
title: Como criar um despejo "limpo" quando solicitado pelo agente de suporte
description: Este artigo fornece informações sobre como criar um despejo "depurado" (backup) do banco de dados e do código pelo administrador do Adobe Commerce quando solicitado a fornecer um por um agente de suporte da Adobe Commerce. Esse despejo exclui os arquivos de mídia para acelerar o processo e resultar em um arquivo muito menor. Todos os dados confidenciais recebem hash ao fazer o backup do banco de dados.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Como criar um despejo &quot;limpo&quot; quando solicitado pelo agente de suporte


## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.3.x, 2.4.x.

## Criar um despejo &quot;depurado&quot;

Crie um despejo &quot;depurado&quot; na página Admin:

1. No Administrador do Commerce, vá para **Sistema** > **Suporte** > **Coletor de Dados**.
1. Clique em **Novo Backup**.
1. Após alguns minutos, clique em **Atualizar Status** (pode demorar mais, repita a cada 5 minutos até ser concluído).
1. Realocar os arquivos de despejo gerados do diretório `/var/support` para o diretório raiz do Adobe Commerce.

Em seguida, você pode fornecer ao Suporte o link de download direto para os arquivos de despejo (o endereço da loja e o nome do arquivo conforme exibido).

Se você tiver problemas ao criar despejos do Administrador, considere usar comandos da CLI conforme descrito em [Executar os utilitários de suporte](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/run-support-utilities) em nossa documentação de desenvolvedor.

## Leitura relacionada

* [Crie um backup completo do banco de dados para o Adobe Commerce na infraestrutura em nuvem](/help/how-to/general/create-database-dump-on-cloud.md) em nossa base de dados de conhecimento de suporte.
