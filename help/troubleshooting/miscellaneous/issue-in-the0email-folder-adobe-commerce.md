---
title: A permissão var/export da pasta emite Adobe Commerce na nuvem
description: Este artigo fornece uma solução para um problema em que você não pode exportar dados do produto devido a um problema de permissões de arquivo no servidor na pasta "var/export/email". Os sintomas incluem exportações de Produto e Catálogo não disponíveis na interface do usuário, mas visíveis ao usar SSH.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# A permissão var/export da pasta emite Adobe Commerce na nuvem

Este artigo fornece uma solução para um problema em que você não pode exportar dados do produto devido a um problema de permissões de arquivo no servidor na pasta `var/export/email`. Os sintomas incluem exportações de Produto e Catálogo não disponíveis na interface do usuário, mas visíveis ao usar SSH.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problema

Não é possível exportar arquivos na pasta `var/export/email` ou `var/export/archive`.
Esta implantação falhou devido a permissões em `var/export/email` ou `var/export/email/archive` porque a pasta de arquivamento é criada por email e se eu apenas fizer a exportação/email (às vezes, ainda há um problema) que não seja adicionar algo à conta para a subpasta `var/export/email/archive`.

<u>Etapas a serem reproduzidas</u>:

No Admin, vá para **Sistema** > *Transferência de Dados* > **Exportar**.
Selecione os arquivos CSV para salvar na pasta `var/export/`.

<u>Resultado esperado</u>:

Os arquivos CSV estão visíveis e podem ser exportados.

<u>Resultado real</u>:

Os arquivos CSV não estão visíveis. Você também vê uma mensagem de permissão negada: *RecursiveDirectoryIterator::__construct(/app/project id>/var/export/email): falha ao abrir o dir: Permissão negada*

Você recebe a mesma mensagem para todos os tipos de exportação: Advanced Pricing, Customer Finances, Customer Main File e Customer Addresses.

## Causa

Isso é causado por uma pasta criada em `/var` que tem permissões imperfeitas: `d-wxrwsr-T`. O bit fixo T significa que os usuários só podem excluir os arquivos que possuem, mas o executável ausente significa que não podem criar arquivos no diretório.

Isso geralmente é notado quando o sistema cria uma pasta chamada `export`, que contém uma pasta chamada `email`, que contém uma pasta chamada `archive`.

Para verificar se o diretório tem essas permissões configuradas incorretamente, execute o seguinte comando no CLI/Terminal:

`ls -ld var/export/`

A saída se as permissões estiverem configuradas incorretamente será:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Solução

Para resolver isso, atualize as permissões das pastas para 777 e, em seguida, todos os arquivos recursivamente, executando os seguintes comandos:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Leitura relacionada

* [Exportar](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-export) em nosso guia do usuário.
