---
title: "Falha na atualização do compositor no Adobe Commerce: tipo de argumento incompatível"
description: Este artigo fornece uma solução para quando a implantação travar devido a um problema com a compilação de código. Esse problema é causado por uma nova versão da dependência de symfony/console (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Falha na atualização do compositor no Adobe Commerce: tipo de argumento incompatível

>[!NOTE]
>
>Este problema foi corrigido na versão mais recente do symfony 4.4.29.

Este artigo fornece uma solução para quando a implantação travar devido a um problema com a compilação de código. Esse problema é causado por uma nova versão da dependência de symfony/console (4.4.27, 4.4.28).

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) e Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* dependência de symfony/console (4.4.27, 4.4.28).

## Problema

Uma nova versão da dependência de symfony/console (4.4.27, 4.4.28) está causando falha no processo de compilação de dependência.

<u>Etapas a serem reproduzidas</u>:

Ao instalar ou atualizar o Adobe Commerce ou executar a atualização do composer, a execução falha com a seguinte mensagem de erro:
*Tipo de argumento incompatível: tipo obrigatório: int. Tipo real: cadeia de caracteres*

## Causa

O problema é causado pela incompatibilidade do código principal do Adobe Commerce com a dependência mais recente de &quot;symfony/console&quot; lançada nas versões 4.4.27 e 4.4.28.

## Solução

O problema será resolvido automaticamente assim que uma nova versão 4.2.29 do symfony/console for lançada (prevista para agosto de 2021).

**Como corrigir no Adobe Commerce no local:**

Adobe Commerce no local 2.4.x

Execute o seguinte comando no CLI/Terminal:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Todos os comerciantes locais do Adobe Commerce 2.3.5+ devem executar o seguinte comando da CLI:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Como corrigir no Adobe Commerce na infraestrutura em nuvem:**

Execute os comandos acima ou atualize para a versão mais recente das ferramentas ECE (ece-tools: 2002.1.7), que estará disponível na quinta-feira, 29 de julho. Para obter etapas, consulte [Nuvem para Adobe Commerce > Atualizar versão das ferramentas ece](https://devdocs.magento.com/cloud/project/ece-tools-update.html) na documentação do desenvolvedor.

A correção completa será lançada no Adobe Commerce (todos os métodos de implantação) 2.4.4.

## Leitura relacionada

* Github: [27 de julho de 2021 Atualização do compositor Tipo de argumento incompatível: Tipo obrigatório: int. Tipo real: cadeia de caracteres](https://github.com/magento/magento2/issues/33595)
