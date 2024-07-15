---
title: executar problema de `setup:static-content:deploy` deployed_version.txt
description: Este artigo fornece uma correção para `deployed_version.txt` não é um erro gravável ao executar o comando `setup:static-content:deploy` manualmente.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# executar problema `setup:static-content:deploy` deployed_version.txt

Este artigo fornece uma correção para o erro `deployed_version.txt` não é gravável ao executar o comando `setup:static-content:deploy` manualmente.

## Problema

Se você seguir as recomendações do Adobe Commerce na infraestrutura da nuvem para usar o [Gerenciamento de Configuração](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (e mover a geração de ativos estáticos para o estágio de compilação para reduzir o tempo de inatividade do site durante a implantação), poderá enfrentar o seguinte erro ao executar o comando `setup:static-content:deploy` manualmente:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Causa

Otimizamos o processo de implantação para diminuir o tempo de inatividade e criamos symlinks para arquivos de ativos estáticos em vez de copiá-los. O local onde os ativos estáticos são armazenados é somente leitura, por isso você recebe a mensagem de erro acima.

É altamente recomendável executar a implantação de conteúdo estático manualmente, pois todos os ativos já foram gerados e não haverá diferença entre os arquivos se você fizer isso manualmente (os arquivos de tema também são somente leitura, não é possível alterá-los). Portanto, essa operação não faz sentido.

## Solução

Se ainda quiser executar a implantação de conteúdo estático, remova os symlinks no diretório `pub/static` e execute o comando `setup:static-content:deploy` novamente:

```
find pub/static/ -maxdepth 1 -type l -delete
```
