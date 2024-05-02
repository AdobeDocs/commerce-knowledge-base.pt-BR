---
title: Solução de problemas de armazenamento de banco de dados no Adobe Commerce
description: Este artigo é uma ferramenta de solução de problemas para clientes no Adobe Commerce que têm problemas com bancos de dados. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas. Dependendo dos sintomas e da configuração, o solucionador de problemas explicará como solucionar problemas de espaço e configuração com bancos de dados.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Solução de problemas de armazenamento de banco de dados no Adobe Commerce

Este artigo é uma ferramenta de solução de problemas para clientes no Adobe Commerce que têm problemas com bancos de dados. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas. Dependendo dos sintomas e da configuração, o solucionador de problemas explicará como solucionar problemas de espaço e configuração com bancos de dados.

## Etapa 1 - Identificar o diretório com um problema de espaço {#step-1}

+++**Você tem um `/tmp` problema causado pela falta de espaço?**

Este fato pode ser indicado por uma série de sintomas, incluindo `/tmp` montagem cheia, site desativado ou não poder aplicar SSH a um nó. Você também pode estar enfrentando erros como _Não há mais espaço no dispositivo (28)_. Para obter uma lista de erros resultantes de `/tmp` por estar cheio, revise [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Ou você tem um `/data/mysql` problema causado pela falta de espaço? Isso também pode ser indicado por uma variedade de sintomas, incluindo interrupção do site, clientes incapazes de adicionar produtos ao carrinho, falha de conexão com o banco de dados e erros da Galeria, como _SQLSTATE\[08S01\]: Falha no link de comunicação: WSREP 1047_. Para obter uma lista de erros resultantes de pouco espaço em disco no MySQL, consulte [O espaço em disco do MySQL é insuficiente no Adobe Commerce na infraestrutura em nuvem](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Se você não tiver certeza se tem um problema de espaço em disco e se tem uma conta do New Relic, vá para a [Página Hosts de monitoramento do New Relic Infrastructure](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). A partir daí, clique no link **Armazenamento** , altere o **Exibições de Gráfico** lista suspensa de 5 a 20 resultados e procure na tabela por alto uso do disco no gráfico ou tabela % de Disco Utilizado. Para obter etapas mais detalhadas, consulte [Monitoramento de infraestrutura New Relic > guia Armazenamento]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Se você tiver algum dos sintomas descritos acima, verifique o estado dos inodes para ter certeza de que isso não está sendo causado por problemas de número de arquivo. Para fazer isso, execute o seguinte comando no CLI/Terminal:\
`df -ih`

O IUse% > 90%?

a. SIM - Isso é causado por ter muitos arquivos. Revise as etapas para remover arquivos com segurança no [Exclua arquivos com segurança quando não houver espaço em disco, Adobe Commerce na infraestrutura em nuvem](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Vá para [Etapa 2](#step-2) após concluir essas etapas. Se quiser solicitar mais espaço, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Verifique o espaço. Executar `df -h | grep mysql` e depois `df -h | grep tmp` no CLI/Terminal para verificar o uso do espaço em disco no `/tmp` e `/data/mysql` diretórios. Vá para [Etapa 3](#step-3).

+++

## Etapa 2 - Verificar o espaço em disco {#step-2}

+++**Verificar o uso do espaço em disco?**

Depois de reduzir o número de arquivos, execute `df -h | grep mysql` e depois `df -h | grep tmp` na CLI/Terminal para verificar o uso do espaço em disco no `/tmp` e `/data/mysql`. É maior que 70% usado para `/tmp` ou `/data/mysql`?

a. SIM - Vá para [Etapa 3](#step-3).
b. NÃO - As consultas podem estar esgotando o armazenamento disponível. Isso pode causar falha no nó, matando a consulta e removendo o `tmp` arquivos. Examine a saída do `SHOW PROCESSLIST;` na CLI do MySQL para consultas que podem ser a causa do problema. [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando mais espaço.

+++

## Etapa 3 - Identificar diretório com alto uso {#step-3}

+++**Qual diretório tem mais de 70% de uso?**

Qual diretório tem mais de 70% de uso? `/tmp` ou `/data/mysql`?

>[!NOTE]
>
>Por padrão, o tmpdir do banco de dados grava em `/tmp`. Para verificar se a configuração do banco de dados ainda está nesse padrão, execute o seguinte comando na CLI do MySQL: `SHOW VARIABLES LIKE "TMPDIR";` Se o banco de dados tmpdir ainda estiver gravando em `/tmp`, você verá `/tmp` na coluna Value.

a) `/tmp` - Vá para [Etapa 4](#step-4). \
b) `/data/mysql` - Vá para [Etapa 5](#step-5).

+++

## Etapa 4 - Solução de problemas /tmp mount full {#step-4}

+++**Solução de problemas de montagem /tmp completa**

[Solução de problemas de montagem /tmp completa para o Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), role para baixo no artigo e experimente as soluções e práticas recomendadas. Em seguida, execute `df -h | grep mysql` e depois `df -h | grep tmp` na CLI/Terminal para verificar o uso do espaço em disco no `/tmp` e `/data/mysql` diretórios\
  &lt; 70% usado?

>[!NOTE]
>
>As soluções em [Solução de problemas de montagem /tmp completa para o Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) são projetadas para comerciantes que não alteraram as variáveis do banco de dados tmpdir, que por padrão grava em `/tmp`. Se você alterou o valor tmpdir, as instruções em [Solução de problemas de montagem /tmp completa para o Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) não vai ajudar.

a. SIM - Você resolveu o problema. \
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando mais espaço.

+++

## Etapa 5 - Verificar padrão {#step-5}

+++**Verificar padrão**

A configuração do banco de dados pode não estar mais no padrão original. Localize a configuração tmpdir do banco de dados executando na CLI do MySQL: `SELECT @@DATADIR;`. Se `/data/mysql/` for emitido, o tmpdir do banco de dados agora está gravando em `/data/mysql/`. Tente aumentar o espaço neste diretório seguindo as etapas em [O espaço em disco do MySQL é insuficiente no Adobe Commerce em nossa infraestrutura em nuvem](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Em seguida, execute `df -h | grep mysql` e depois `df -h | grep tmp` na CLI/Terminal para verificar o uso do espaço em disco no `/data/mysql` e `/tmp`.\
  &lt; 70% usado?

a. SIM - Você resolveu o problema. \
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando mais espaço.

+++

[Voltar à Etapa 1](#step-1)
