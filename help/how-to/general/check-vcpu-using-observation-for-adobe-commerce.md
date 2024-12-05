---
title: Exibir a camada de vCPU do ambiente em seu cluster no Adobe Commerce
promoted: true
description: Este artigo explica como verificar a alocação de camada do vCPU usando a guia New Relic Infra em Observation for Adobe Commerce. Observação para Adobe Commerce é um nerdlet do New Relic que mostra o estado do site do Adobe Commerce, as visualizações de tempo atuais e anteriores.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: ffb7b597d38eaed4b66e23ea533c275746e7181a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Exibir a camada de vCPU do ambiente em seu cluster no Adobe Commerce

Este artigo explica como verificar a alocação de camada do vCPU usando a guia New Relic Infra em Observation for Adobe Commerce. Observação para Adobe Commerce é um nerdlet do New Relic que mostra o estado do site do Adobe Commerce, as visualizações de tempo atuais e anteriores.

## Produtos e versões afetados:

Adobe Commerce na infraestrutura em nuvem 2.4.3 - 2.4.6

## Verifique a alocação de camada do vCPU com a Observação para Adobe Commerce:

Para acessar e fazer logon no nerdlet New Relic Observation for Adobe Commerce:

1. Na página inicial do New Relic, clique em **Aplicativos**.
1. Clique em **Observação para Adobe Commerce**.
1. A observação para o nerdlet do Adobe Commerce é aberta.
1. Clique na lista suspensa **Selecionar uma conta** e selecione uma conta.
1. É possível preencher a ID do projeto, o número da conta da New Relic ou o nome da conta, ou navegar pela lista de contas.
1. Clique no menu suspenso azul claro com o ícone de relógio (na direção da parte superior direita da janela do nerdlet).
1. Se estiver tentando identificar a causa de um evento/problema, selecione um horário antes da data e hora do ticket para ver se houve eventos/dados anteriores. Você pode usar os intervalos de tempo predefinidos ou definir um intervalo de tempo personalizado selecionando **Definir personalizado**.
1. Nas guias, clique em **Infra**. Há três gráficos de níveis do vCPU:
   * O primeiro gráfico mostra uma exibição de camada do vCPU **durante a linha do tempo MAIOR QUE 2 semanas (Você precisará selecionar uma linha do tempo MAIOR que 2 semanas). NOTA: a taxa de amostragem será por dia. Se ocorrerem upsizing/downsize de cluster em um dia, o tamanho da camada final será exibido no dia seguinte**.
   * O segundo gráfico mostra a exibição de camada do **vCPU na linha do tempo (é necessário selecionar uma linha do tempo MAIOR que 24 horas, mas não maior que 2 semanas)**.
   * O terceiro gráfico mostra a exibição da camada do **vCPU sobre a linha do tempo POR NÓ. Deve observar a linha do tempo MENOS de 24 horas**.
