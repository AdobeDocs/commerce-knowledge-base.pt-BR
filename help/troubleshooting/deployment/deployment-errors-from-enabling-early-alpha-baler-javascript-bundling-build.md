---
title: Erros de implantação ao ativar o módulo Early-Alpha Baler
description: O comerciante enfrenta erros de implantação ao usar o módulo Baler em um ambiente de produção, pois o recurso está atualmente no estágio inicial de desenvolvimento alfa.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Erros de implantação ao ativar o módulo Early-Alpha Baler

O comerciante enfrenta erros de implantação ao usar o módulo Baler em um ambiente de produção, pois o recurso está atualmente no estágio inicial de desenvolvimento alfa.

>[!WARNING]
>
>O pacote JavaScript Early-alpha Baler não está pronto para uso de produção e é usado por sua conta e risco.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.x e 2.4.x.
* Adobe Commerce no local 2.3.x e 2.4.x.

## Problema

Não recomendamos que os comerciantes usem o módulo Baler em um ambiente de produção, pois ele está atualmente no estágio inicial de desenvolvimento alfa. Usá-lo pode resultar em erros de implantação.

<u>Etapas a serem reproduzidas</u>:

1. O comerciante tenta inserir a variável **SCD\_USE\_BALER** no estágio de criação da variável `.magento.env.yaml` que ativa o pacote de empacotamento Baler Javascript.
1. O comerciante também acrescenta a dependência do compositor Baler: `"magento/module-baler": "1.0.0-alpha"` para `require` seção de `composer.json`.

<u>Resultado esperado</u>:

Implantação bem-sucedida.

<u>Resultado real</u>:

O comerciante vê a seguinte mensagem de erro nos logs de implantação na nuvem, que é `<project home>/var/log/cloud.log`, no estágio de implantação de conteúdo estático:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Causa

O módulo Baler está atualmente no estágio inicial de desenvolvimento alfa e o processo de instalação da extensão Baler é complexo.

## Solução

Você pode revisar a documentação existente do Alpha Baler em [Github/Magento/Baler/Introdução ao alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md). No entanto, ele não está pronto para uso de produção e é usado por sua conta e risco. Em vez disso, é recomendável mesclar ou agrupar arquivos Javascript (JS) usando o agrupamento incorporado do Adobe Commerce (agrupamento básico) para otimização de arquivos.

* Você pode ativar a mesclagem ou o agrupamento no Administrador (a mesclagem e o agrupamento não podem ser ativados ao mesmo tempo): **Lojas** > **Configurações** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações do JavaScript**.
* Você também pode ativar o agrupamento incorporado do Adobe Commerce (agrupamento básico) na linha de comando: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Para saber mais, consulte [Otimização de arquivos CSS e Javascript no Adobe Commerce na infraestrutura em nuvem e no Adobe Commerce no local](https://support.magento.com/hc/en-us/articles/360044482152).
