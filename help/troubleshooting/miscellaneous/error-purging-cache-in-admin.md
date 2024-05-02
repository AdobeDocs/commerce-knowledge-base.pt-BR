---
title: Erro ao limpar o cache no Commerce Admin
description: '"Este artigo explica como identificar a causa de uma mensagem de erro que ocorre ao limpar o cache no Administrador do Commerce. Ao tentar limpar o cache por meio do Administrador, você recebe a seguinte mensagem:'''
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Erro ao limpar o cache no Commerce Admin

Este artigo explica como identificar a causa de uma mensagem de erro que ocorre ao limpar o cache no Commerce Admin. Ao tentar limpar o cache por meio do Administrador, você recebe a seguinte mensagem:
*O arquivo /app/project-id/pub/media/catalog/product/cache/diretory/filename&quot; não pode ser excluído. Aviso!unlink(/app/project id/pub/media/catalog/product/cache/diretory/filename): esse arquivo ou diretório não existe*

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problema

Ao tentar limpar o cache por meio do Administrador, você recebe uma mensagem de erro.

<u>Etapas a serem reproduzidas:</u>

1. No Administrador, acesse **Sistema** > **Ferramentas** > **Gerenciamento de cache**.
1. Selecione qualquer uma das opções de limpeza de cache.

<u>Resultado esperado:</u>

Você liberou o cache do Adobe Commerce com êxito sem erros.

<u>Resultado real:</u>

Você recebe o erro &quot;O arquivo não pode ser excluído&quot;.

## Causa

O erro está relacionado a um atraso entre o momento em que a operação de limpeza de cache foi iniciada e o momento em que foi relatada como concluída.

## Solução

1. Confirme se os arquivos mencionados no erro não estão presentes no servidor (verificando se a limpeza do cache foi bem-sucedida):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Se você vir a seguinte saída:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

houve uma tentativa de limpar os arquivos quando a operação já tinha sido concluída. Isso não é um erro; é um problema de simultaneidade de mensagens que deve ocorrer às vezes. Não há problemas a serem solucionados.
No entanto, se a saída mostrar que os arquivos ainda estão no cache, será necessário [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Leitura relacionada

* [Gerenciamento de cache](https://docs.magento.com/user-guide/system/cache-management.html) na documentação do desenvolvedor.
