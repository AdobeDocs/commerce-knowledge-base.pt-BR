---
title: Falha ao carregar o site devido ao modo de manutenção deixado habilitado
description: "Este artigo fornece uma correção para quando o site não é carregado porque o modo de manutenção está ativado ou não foi desativado automaticamente. Você pode receber uma mensagem de erro: *Serviço temporariamente indisponível O servidor está temporariamente incapaz de atender à sua solicitação devido a tempo de inatividade de manutenção ou problemas de capacidade.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Falha ao carregar o site devido ao modo de manutenção deixado habilitado

Este artigo fornece uma correção para quando o site não é carregado porque o modo de manutenção está ativado ou não foi desativado automaticamente. Você pode receber uma mensagem de erro: *Serviço temporariamente indisponível O servidor está temporariamente incapaz de atender à sua solicitação devido a problemas de capacidade ou tempo de inatividade de manutenção.*

## Versões e produtos afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x

## Problema

O modo de manutenção faz parte do processo de implantação. No entanto, se ele tiver sido ativado automaticamente e não tiver sido desativado, ou se o modo de manutenção ativado pelo comerciante manualmente e se tiver esquecido de ser desativado, pode causar uma falha na implantação.

## Causa

A ativação do modo de manutenção impede o carregamento do site.

## Solução

Para verificar o status atual do modo de manutenção, execute o seguinte comando na CLI:

```
bin/magento maintenance:status
```

Para desativar o modo de manutenção, execute o seguinte comando na CLI:

```
bin/magento maintenance:disable
```

## Leitura relacionada

Para saber quando usar o modo de manutenção, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor.
