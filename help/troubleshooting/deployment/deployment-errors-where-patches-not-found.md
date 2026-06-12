---
title: Erros de patch não encontrado durante implantação ou aplicação manual
description: 'Este artigo fornece uma solução para o problema em que você vê um erro *Próximos patches não foram encontrados: MDVA-XXXXX, ACSD-XXXXX. Verifique a disponibilidade desses patches para a versão atual do Magento usando o comando ''status''*.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 180f0e00ec1a2c6c3bd2ebca4dafe387c7bb3852
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Erros de patch não encontrado durante implantação ou aplicação manual

Este artigo fornece uma solução para o problema que ocorria ao atualizar sua instância durante a falha da implantação e você vê um erro nos logs de implantação: *Os próximos patches não foram encontrados: MDVA-XXXXX, ACSD-XXXXX. Verifique a disponibilidade desses patches para a versão atual do Magento usando o comando &quot;status&quot;*.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Você está tendo um erro ao atualizar o Adobe Commerce: *Os próximos patches não foram encontrados*.

## Causa

Os patches aplicados anteriormente para suas versões mais antigas não se aplicam ou não estão mais disponíveis para sua nova versão.

Esse problema também pode ocorrer quando o pacote da Ferramenta de Patches de Qualidade (`magento/quality-patches`) instalado está desatualizado.

Por exemplo:

Caso 1:
* Um patch pode ter sido originalmente disponível para 2.4.7-p9 no QPT 1.1.71
* Uma versão mais recente do QPT (por exemplo, 1.1.72) pode adicionar suporte para 2.4.7-p10
* Se o cliente atualizar o Commerce para 2.4.7-p10, mas mantiver uma versão mais antiga do QPT instalada, o QPT pode não reconhecer que existe uma variante de patch compatível para 2.4.7-p10

Caso 2:
* Um patch pode ter sido adicionado no QPT 1.1.72
* Se o cliente mantém uma versão mais antiga do QPT instalada, o QPT não reconhecerá que o patch existe

Nesses casos, a aplicação do patch pode falhar com uma mensagem como:

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

Isso acontece porque a versão instalada do QPT não pode mapear a versão atual do Commerce para uma versão aplicável do patch.

## Solução

Esse problema não está limitado a implantações que aplicam patches por meio do `.magento.env.yaml`. O mesmo problema subjacente também pode ocorrer ao aplicar um patch manualmente com:

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

Por exemplo:

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

Nesse caso, o patch não está disponível para a versão do Adobe Commerce instalada no ambiente em que o comando está sendo executado.

1. Verifique o arquivo `.magento.env.yaml` na seção QUALITY_PATCHES, por exemplo,

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. Pesquise as IDs de patch nas [Notas de versão de Patches de qualidade](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=pt-BR) para verificar se cada uma pode ser aplicada à nova versão do Adobe Commerce para a qual você está atualizando.
1. Se o patch não se aplicar à nova versão do Adobe Commerce que você deseja atualizar, remova a ID do patch do arquivo `.magento.env.yaml`.
1. Depois de ter revisado todas as IDs de patch indicadas pelo erro, envie as alterações para push e reimplante.

## Leitura relacionada

* [Aplique patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR#apply-a-patch-in-a-local-environment) no Guia de Infraestrutura do Commerce na Nuvem.
