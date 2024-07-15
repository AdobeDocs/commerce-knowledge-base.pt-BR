---
title: Erros de implantação em que patches não foram encontrados
description: "Este artigo fornece uma solução para o problema em que você vê um erro *Os próximos patches não foram encontrados: MDVA-XXXXX, ACSD-XXXXX. Verifique com o comando 'status' a disponibilidade desses patches para a versão atual do Magento*."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Erros de implantação em que patches não foram encontrados

Este artigo fornece uma solução para o problema que ocorria ao atualizar sua instância durante a falha da implantação e você vê um erro nos logs de implantação: *Os próximos patches não foram encontrados: MDVA-XXXXX, ACSD-XXXXX. Verifique com o comando &quot;status&quot; a disponibilidade desses patches para a versão atual do Magento*.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problema

Você está tendo um erro ao atualizar o Adobe Commerce: *Os próximos patches não foram encontrados*.

## Causa

Os patches aplicados anteriormente para suas versões mais antigas não se aplicam ou não estão mais disponíveis para sua nova versão.

## Solução

1. Verifique o arquivo `.magento.env.yaml` na seção QUALITY_PATCH, por exemplo,

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Pesquise as IDs de patch nas [Notas de versão de Patches de qualidade](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) para verificar se cada uma pode ser aplicada à nova versão do Adobe Commerce para a qual você está atualizando.
1. Se o patch não se aplicar à nova versão do Adobe Commerce que você deseja atualizar, remova a ID do patch do arquivo `.magento.env.yaml`.
1. Depois de ter revisado todas as IDs de patch indicadas pelo erro, envie as alterações para push e reimplante.

## Leitura relacionada

* [Aplique patches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) no Guia de Infraestrutura do Commerce na Nuvem.
