---
title: Verificando ataque de DDoS a partir da CLI
description: Este artigo fala sobre a questão de como tentar verificar se há ataques de DDoS (Negação de Serviço Distribuído) na CLI (Interface de Linha de Comando) do seu servidor.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Verificando ataque de DDoS a partir da CLI

Este artigo fala sobre a questão de como tentar verificar se há ataques de DDoS (Negação de Serviço Distribuído) na CLI (Interface de Linha de Comando) do seu servidor.

## Produtos e versões afetados

* Adobe Commerce, todas as versões
* Magento Open Source, todas as versões

## Problema

Seu site é lento e você não tem acesso a nenhuma outra ferramenta de aplicativo de análise, além da CLI, para verificar um possível ataque de DDoS. Os sintomas de um ataque de DDoS podem variar amplamente dependendo da configuração da rede, do software usado, etc.

No entanto, é recomendável utilizar produtos de software de análise especificamente projetados para ajudar a identificar ataques de DDoS.

## Causa

Há várias causas possíveis para um site lento, incluindo um servidor de desempenho lento, alto uso de CPU ou configuração incorreta em scripts, código ou hardware barato. Às vezes, pode ser devido a um ataque de DDoS. Duas das ferramentas básicas que você tem para verificar se há um ataque de DDoS são os registros do Adobe Commerce e a CLI.

Novamente, é importante observar que o uso de software especificamente projetado para identificar ataques de DDoS seria muito útil em sua investigação.

## Etapas da solução

1. Verifique os registros do Adobe Commerce para ver se há algo além de um ataque de DDoS ocorrendo. Para obter mais informações, consulte os seguintes artigos na documentação do desenvolvedor:
   * [Locais de logs Adobe Commerce e Magento Open Source](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)
   * [Adobe Commerce em locais de logs de infraestrutura em nuvem](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)
1. Comece a usar sua CLI para verificar todas as suas conexões atuais com a Internet usando o comando `netstat`: `netstat -na`. Isso exibe todas as conexões ativas estabelecidas com o servidor. Aqui você pode notar muitas conexões provenientes do mesmo endereço IP.
1. Para restringir ainda mais suas conexões estabelecidas, apenas aquelas que se conectam na porta 80 (a porta http do seu site), de modo que você possa classificar e reconhecer muitas conexões de um endereço IP ou grupo de endereços IP, use este comando: `netstat -an | grep :80 | sort`. Você pode repetir o mesmo comando para https na porta 443: `netstat -an | grep :443 | sort`. Outra opção é estender o comando original para ambas as portas 80 e 443: `netstat -an | egrep ":80|:443" | sort`.
1. Para ver se muitos `SYNC_REC` ativos estão ocorrendo no servidor, use o comando:     `netstat -n -p|grep SYN_REC | wc -l`     Normalmente, esse número é menor que 5, mas pode ser muito maior para um ataque de DDoS, embora para alguns servidores um número maior possa ser uma condição normal.
1. Para listar todos os endereços IP que enviam status `SYNC_REC`, use o comando: `netstat -n -p | grep SYN_REC | sort -u`.
1. Para listar ainda mais todos os endereços IP exclusivos que enviam status `SYNC_REC`, use o comando: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Você também pode usar o comando `netstat` para contar e calcular o número de conexões que cada endereço IP faz ao seu servidor: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Para listar a contagem de conexões de protocolo UDP ou TCP conectadas ao seu servidor, use o comando: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Para verificar as conexões estabelecidas, em vez de apenas todas as conexões, e exibir a contagem de conexões para cada endereço IP, use o comando: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Para mostrar as contagens de conexão listadas pelo endereço IP para a porta 80, use o comando: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Certifique-se de ter alguém para fornecer a análise adequada dos dados encontrados para determinar se você está de fato tendo um ataque de DDoS. Usar os comandos `netstat` da CLI do servidor nessas etapas acima ajudará a analisar se você está enfrentando um ataque de DDoS, mas usar produtos de análise de software especificamente projetados para ajudar a identificar ataques de DDoS, juntamente com uma análise adequada, são suas melhores ferramentas para identificar ameaças de DDoS.

Se você descobrir que está sob ataque de DDoS, as etapas que pode tomar dependem da sua configuração de rede e como o ataque de DDoS está ocorrendo, mas a recomendação geral é entrar em contato com seu ISP, obter um novo endereço IP para o seu servidor e/ou consultar profissionais de TI qualificados em lidar com problemas de DDoS para analisar e aconselhar sobre sua situação específica.

## Leituras relacionadas em nossa documentação do desenvolvedor:

* [Proteção de DDoS](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-fastly.html#ddos-protection)
* [Usando comandos CLI](https://devdocs.magento.com/guides/v2.3/config-guide/deployment/pipeline/example/cli.html)
* [CLI da nuvem para o Commerce](https://devdocs.magento.com/guides/v2.3/cloud/reference/cli-ref-topic.html)
