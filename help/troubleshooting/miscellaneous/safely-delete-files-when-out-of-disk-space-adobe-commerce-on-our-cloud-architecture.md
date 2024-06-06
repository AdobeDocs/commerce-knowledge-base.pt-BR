---
title: Exclua arquivos com segurança quando o disco ficar sem espaço no Adobe Commerce na infraestrutura de nuvem
description: Este artigo fornece uma solução para quando você ficar sem espaço em disco e precisar remover arquivos com segurança. Antes de considerar essa ação, revise [Gerenciar espaço em disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html#no-space-left) em nossa documentação do desenvolvedor. Se as etapas nesse artigo não forem apropriadas para você ou não resolverem o problema, analise as etapas neste artigo.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 86515936f72bbd0a5778cb81f665993ed91e4707
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Exclua arquivos com segurança quando o disco ficar sem espaço no Adobe Commerce na infraestrutura de nuvem

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.2 - 2.4.7
* Isso é específico para clusters Pro dedicados. Os ambientes de Início e Integração são de nó único e não têm o `/data/exports` diretório.

## Sinais de pouco espaço em disco

Os sinais de que você está ficando sem espaço em disco podem ser implantação paralisada, avisos de disco cheio e desempenho insatisfatório.
Para ver a quantidade de espaço em disco usada pelo sistema de arquivos, execute o seguinte comando no CLI/Terminal:

`df -h`


## Como excluir arquivos com segurança para aumentar o espaço em disco

É possível excluir arquivos dos pontos de montagem do aplicativo, a partir de `/app` caminho ou através `/mnt/shared`. São duas maneiras diferentes de acessar os mesmos arquivos.

>[!WARNING]
>
>**Nunca modifique ou exclua o conteúdo de`/data/exports`**.
>
>`/data/exports` é o armazenamento subjacente por trás do sistema de arquivos compartilhado, gerenciado pelo GlusterFS.
>
>O sistema de arquivos contém não apenas o conteúdo do arquivo, mas metadados sobre o estado do sistema de arquivos para permitir a sincronização entre os nós do cluster. **A alteração ou exclusão de arquivos diretamente neste sistema de arquivos corromperá o sistema de arquivos compartilhado, exigindo reparos extensos ou recuperação de dados.**

Para localizar os maiores arquivos que podem ser bons candidatos para limpeza, execute o seguinte comando (em projetos grandes ou ocupados, pode levar até uma hora):

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

A saída do comando conterá uma lista dos maiores arquivos e diretórios com seus tamanhos especificados.

## Leitura relacionada

Em nossa base de conhecimento de suporte:

* [Aumentar espaço em disco para o ambiente de integração na nuvem](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Pouco espaço em disco](/help/troubleshooting/miscellaneous/low-disk-space.md)

Em nossa documentação do desenvolvedor:

* [Gerenciar espaço em disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html)
