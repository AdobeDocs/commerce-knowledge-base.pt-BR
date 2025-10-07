---
title: Solução de problemas de armazenamento de banco de dados no Adobe Commerce
description: Este artigo é uma ferramenta de solução de problemas para clientes no Adobe Commerce que têm problemas com bancos de dados. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas. Dependendo dos sintomas e da configuração, o solucionador de problemas explicará como solucionar problemas de espaço e configuração com bancos de dados.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Solução de problemas de armazenamento de banco de dados no Adobe Commerce

Este artigo é uma ferramenta de solução de problemas para clientes no Adobe Commerce que têm problemas com bancos de dados. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas. Dependendo dos sintomas e da configuração, o solucionador de problemas explicará como solucionar problemas de espaço e configuração com bancos de dados.

## Etapa 1 - Identificar o diretório com um problema de espaço {#step-1}

+++**Você tem um problema de `/tmp` causado por falta de espaço?**

Isso pode ser indicado por uma variedade de sintomas, incluindo a montagem `/tmp` estar cheia, site inativo ou não poder aplicar SSH a um nó. Você também pode estar enfrentando erros como _Não há espaço disponível no dispositivo (28)_. Para obter uma lista de erros resultantes de `/tmp` estar cheio, consulte [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Ou você tem um problema `/data/mysql` causado por falta de espaço? Isso também pode ser indicado por uma variedade de sintomas, incluindo paralisação do site, clientes incapazes de adicionar produtos ao carrinho, falha de conexão ao banco de dados e erros da Galeria, como _SQLSTATE\[08S01\]: Falha de link de comunicação: 1047 WSREP_. Para obter uma lista de erros resultantes de pouco [!DNL MySQL] de espaço em disco, consulte [[!DNL MySQL] pouco espaço em disco na infraestrutura de nuvem do Adobe Commerce](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806).

Se você não tiver certeza se tem um problema de espaço em disco e se tem uma conta do New Relic, vá para a [página Hosts de monitoramento do New Relic Infrastructure](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). A partir daí, clique na guia **Armazenamento**, altere o menu suspenso **Exibições de Gráficos** de 5 para 20 resultados e procure na tabela um alto uso do disco no gráfico ou tabela % de Disco Usado. Para obter etapas mais detalhadas, consulte [Monitoramento de Infraestrutura New Relic > guia Armazenamento]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Se você tiver algum dos sintomas descritos acima, verifique o estado dos inodes para ter certeza de que isso não está sendo causado por problemas de número de arquivo. Para fazer isso, execute o seguinte comando no CLI/Terminal:\
`df -ih`

O IUse% > 90%?

a. SIM - Isso é causado por ter muitos arquivos. Revise as etapas para remover arquivos com segurança no [Exclua arquivos com segurança quando não houver espaço em disco, Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26889). Prossiga para a [Etapa 2](#step-2) depois de concluir essas etapas. Se quiser solicitar mais espaço, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Verifique o espaço. Execute `df -h | grep mysql` e depois `df -h | grep tmp` no CLI/Terminal para verificar o uso de espaço em disco nos diretórios `/tmp` e `/data/mysql`. Vá para [Etapa 3](#step-3).

+++

## Etapa 2 - Verificar o espaço em disco {#step-2}

+++**Verificar uso do espaço em disco?**

Depois de reduzir o número de arquivos, execute `df -h | grep mysql` e depois `df -h | grep tmp` na CLI/Terminal para verificar o uso do espaço em disco em `/tmp` e `/data/mysql`. Mais de 70% é usado para `/tmp` ou `/data/mysql`?

a. SIM - Continue na [Etapa 3](#step-3).
b. NÃO - As consultas podem estar esgotando o armazenamento disponível. Isso pode causar falha no nó, matando a consulta e removendo os arquivos `tmp`. Examine a saída do `SHOW PROCESSLIST;` na CLI do [!DNL MySQL] para consultas que podem ser a causa do problema. [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando mais espaço.

+++

## Etapa 3 - Identificar diretório com alto uso {#step-3}

+++**Qual diretório tem mais de 70% de uso?**

Qual diretório tem mais de 70% de uso? `/tmp` ou `/data/mysql`?

>[!NOTE]
>
>Por padrão, o tmpdir do banco de dados grava em `/tmp`. Para verificar se a configuração do banco de dados ainda está nesse padrão, execute o seguinte comando na CLI do [!DNL MySQL]: `SHOW VARIABLES LIKE "TMPDIR";` Se o tmpdir do banco de dados ainda estiver gravando em `/tmp`, você verá `/tmp` na coluna Valor.

a. `/tmp` - Continue na [Etapa 4](#step-4). \
b. `/data/mysql` - Continue na [Etapa 5](#step-5).

+++

## Etapa 4 - Solução de problemas /tmp mount full {#step-4}

+++**Solução de problemas /tmp mount full**

[Solução de problemas /tmp mount completo para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), role para baixo no artigo e experimente as soluções e práticas recomendadas. Em seguida, execute `df -h | grep mysql` e depois `df -h | grep tmp` no CLI/Terminal para verificar o uso de espaço em disco nos diretórios `/tmp` e `/data/mysql`\
  &lt; 70% usado?

>[!NOTE]
>
>As soluções em [Solução de problemas /tmp mount full para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) foram projetadas para comerciantes que não alteraram as variáveis para tmpdir de banco de dados, que por padrão grava em `/tmp`. Se você alterou o valor tmpdir, as instruções em [Solução de problemas /tmp mount full for Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) não ajudarão.

a. SIM - Você resolveu o problema. \
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando mais espaço.

+++

## Etapa 5 - Verificar padrão {#step-5}

+++**Verificar padrão**

A configuração do banco de dados pode não estar mais no padrão original. Localize a configuração tmpdir do banco de dados executando na CLI [!DNL MySQL]: `SELECT @@DATADIR;`. Se `/data/mysql/` for gerado, o tmpdir do banco de dados agora está gravando em `/data/mysql/`. Tente aumentar o espaço neste diretório seguindo as etapas em [[!DNL MySQL] o espaço em disco é insuficiente no Adobe Commerce em nossa infraestrutura de nuvem](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806). Em seguida, execute `df -h | grep mysql` e depois `df -h | grep tmp` no CLI/Terminal para verificar o uso de espaço em disco em `/data/mysql` e `/tmp`.\
  &lt; 70% usado?

a. SIM - Você resolveu o problema. \
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando mais espaço.

+++

[Voltar à Etapa 1](#step-1)

## Leitura relacionada

* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
