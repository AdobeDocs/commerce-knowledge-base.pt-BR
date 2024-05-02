---
title: O relatório da Ferramenta de verificação de segurança está em branco
description: Este artigo fornece uma correção para o problema em que a Ferramenta de verificação de segurança mostra uma página em branco em vez do relatório real. Para resolvê-lo, talvez seja necessário adicionar os IPs usados pela Ferramenta ao arquivo de Inclui na lista de permissões de firewall.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# O relatório da Ferramenta de verificação de segurança está em branco

Este artigo fornece uma correção para o problema em que a Ferramenta de verificação de segurança mostra uma página em branco em vez do relatório real. Para resolvê-lo, talvez seja necessário adicionar os IPs usados pela Ferramenta ao arquivo de Inclui na lista de permissões de firewall.

## Produtos e versões afetados:

* Adobe Commerce (todos os métodos de implantação) e Magento Open Source, todas as versões

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Configure a Ferramenta de verificação de segurança para verificar seu site, conforme descrito em [Verificação de segurança](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) em nosso guia do usuário.
1. Na coluna Ações, selecione **Executar verificação**.

<u>Resultados esperados</u>:

Visualizar a notificação de conclusão do relatório e a capacidade de abrir o relatório.

<u>Resultados reais</u>:

Nenhuma notificação e nenhum relatório disponível.

## Causa

Esse problema pode ocorrer porque a Ferramenta de verificação de segurança não conseguiu acessar seu site. Isso significa que o site está inativo e não pode ser acessado de forma alguma ou que a Ferramenta de verificação de segurança está sendo bloqueada.

## Solução

Tente abrir seu site.

* Incluir na lista de permissões Se a página for carregada com sucesso, talvez seja necessário adicionar os IPs usados pelas Ferramentas de verificação de segurança ao arquivo de firewall. Os seguintes IPs são usados: 52.87.98.44, 34.196.167.176, 3.218.25.102 nas portas 80 e 443.
* Se o site não carregar e retornar a variável *&quot;Houve um erro ao processar sua solicitação&quot;* verifique se há possíveis erros no seu site.

## Leitura relacionada

* [Ativar e iniciar](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan) na documentação do desenvolvedor.
* [Verificação de segurança](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) em nosso guia do usuário.
