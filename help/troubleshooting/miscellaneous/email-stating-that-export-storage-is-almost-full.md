---
title: Email informando que o armazenamento de exportações está quase cheio
description: Este artigo fornece uma solução para o problema em que você recebe um e-mail informando que o armazenamento de exportações está quase cheio.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Email informando que o armazenamento de exportações está quase cheio

Este artigo fornece uma solução para o problema em que você recebe um e-mail informando que o armazenamento de exportações está quase cheio.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você recebe um email com o seguinte conteúdo, mas não consegue localizar a pasta *exportações*:

*Nosso monitoramento detectou que o armazenamento &#39;exportações&#39; no cluster XXX está cerca de &#39;85%&#39; cheio.*
*Se necessário, revise o uso, faça uma limpeza ou solicite um upsize.*
*Além disso, observe que tentaremos um upsize automaticamente quando o armazenamento atingir o nível de limite crítico.*

## Causa

O alerta se refere ao sistema de arquivos de armazenamento de exportações, que é o volume do disco onde a mídia e outros dados de arquivos são armazenados. Normalmente, este sistema de arquivos é montado em `/data/exports`. O alerta não indica a presença de um único diretório chamado literalmente exportações.

Para confirmar a que o alerta se refere, verifique o uso do armazenamento de exportações:

* Execute `df -h | grep exports` e o exemplo de saída a seguir será exibido:

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* Neste exemplo, `/data/exports` é o principal sistema de arquivos de exportações:

   * 50 GB no total
   * 38 GB usados
   * 12 GB disponíveis (77% de utilização)

* `/data/exports/shared` é uma montagem `tmpfs` (na memória) usada para dados compartilhados e não contribui significativamente para a pressão do disco.

Isso confirma que o alerta é disparado pela utilização geral do disco de `/data/exports`, não por uma única pasta chamada Exportações.

Se o `/data/exports` mostrar alta utilização, diretórios grandes nesse sistema de arquivos — como pub/mídia ou outros locais de arquivos personalizados — normalmente serão responsáveis pelo aumento no uso.

## Solução

Siga estas etapas para revisar, limpar e validar o uso do armazenamento de exportações.

1. Execute o comando `df -h | grep exports` para verificar o uso atual do sistema de arquivos de armazenamento de exportações. Revise a coluna **Use%** para `/data/exports`:

   * Se o uso for de 70 a 85%, comece a planejar a limpeza.
   * Se o uso for superior a 90%, tome providências imediatamente para evitar falhas de gravação ou impacto no serviço.

1. Identifique diretórios que consomem espaço significativo em disco em `/data/exports` executando:

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   Os locais típicos onde o armazenamento de arquivos provavelmente será preenchido são `pub/media/catalog/product/cache` ou `var/log` pastas.

1. Limpar arquivos com base no ambiente:

   * Remova primeiro arquivos de exportação, logs ou dados temporários antigos ou não utilizados.
   * Em ambientes não relacionados à produção, geralmente é possível remover mídias de teste ou artefatos antigos de forma mais agressiva.
   * Em ambientes de produção, fale com a equipe antes de excluir qualquer mídia ou arquivo essencial aos negócios.

1. Após a limpeza, execute o seguinte comando `df -h | grep exports` para confirmar se o valor **Use%** para `/data/exports` caiu para um nível operacional seguro.

## Leitura relacionada

[Verifique os clusters dedicados](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) em nossa base de dados de conhecimento de suporte.
