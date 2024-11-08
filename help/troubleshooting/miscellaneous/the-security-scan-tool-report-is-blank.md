---
title: O relatório da Ferramenta de verificação de segurança está em branco
description: Este artigo fornece uma correção para o problema em que a Ferramenta de verificação de segurança mostra uma página em branco em vez do relatório real. Para resolvê-lo, talvez seja necessário adicionar os IPs usados pela Ferramenta ao arquivo de Inclui na lista de permissões de firewall.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Configure a Ferramenta de Verificação de Segurança para verificar seu site, conforme descrito em [Verificação de Segurança](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) em nosso guia do usuário.
1. Na coluna Ações, selecione **Executar Verificação**.

<u>Resultados esperados</u>:

Visualizar a notificação de conclusão do relatório e a capacidade de abrir o relatório.

<u>Resultados reais</u>:

Nenhuma notificação e nenhum relatório disponível.

## Causa

Esse problema pode ocorrer porque a Ferramenta de verificação de segurança não conseguiu acessar seu site. Isso significa que o site está inativo e não pode ser acessado de forma alguma ou que a Ferramenta de verificação de segurança está sendo bloqueada.

## Solução

Tente abrir seu site.

* Incluir na lista de permissões Se a página for carregada com sucesso, talvez seja necessário adicionar os IPs usados pelas Ferramentas de verificação de segurança ao arquivo de firewall. Os seguintes IPs são usados: 52.87.98.44, 34.196.167.176, 3.218.25.102 nas portas 80 e 443.
* Se o site não carregar e retornar a mensagem *&quot;Houve um erro ao processar sua solicitação&quot;*, verifique se há possíveis erros no site.

## Leitura relacionada

* [Ativar e iniciar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview) em nossa documentação de desenvolvedor.
* [Verificação de segurança](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) em nosso guia do usuário.
