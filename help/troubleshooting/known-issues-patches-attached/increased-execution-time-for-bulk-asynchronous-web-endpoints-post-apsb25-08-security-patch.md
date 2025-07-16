---
title: Maior tempo de execução para endpoints da Web assíncronos em massa após o patch de segurança APSB25-08
description: Este artigo fornece uma correção para o problema em que as solicitações de POST rest/all/async/bulk/V1/products para mais de 1000 entradas têm um tempo de execução significativamente maior após a aplicação do patch de segurança APSB25-08.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Maior tempo de execução para todos os endpoints da Web assíncronos em massa após o patch de segurança APSB25-08

Este artigo fornece um hotfix para todos os pontos de extremidade da Web assíncronos em massa, como `POST rest/all/async/bulk/V1/products` com mais de 1000 entradas, que estão enfrentando tempos de execução significativamente maiores após a aplicação do patch de segurança APSB25-08.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (todos os métodos de implantação) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11

* Adobe Commerce (todos os métodos de implantação) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (todos os métodos de implantação) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (todos os métodos de implantação) 2.4.8

## Problema

Depois de aplicar o patch de segurança APSB25-08, `POST rest/all/async/bulk/V1/products` solicitações com mais de 1000 entradas estão demorando significativamente mais para serem executadas.

<u>Etapas a serem reproduzidas</u>:

1. Faça uma solicitação `POST rest/all/async/bulk/V1/products` com mais de 1000 entradas (nome, SKU e descrição são suficientes).
1. Anote o tempo gasto para a solicitação.
1. Aplique o patch de segurança APSB25-08 e limpe os dados gerados e o cache usando o `se:di:co`.
1. Executar `bin/magento c:f`.
1. Acesse a loja para garantir que o cache e os arquivos gerados estejam em vigor.
1. Repita a solicitação da etapa 1.
1. Observe o aumento do tempo gasto com a solicitação.
1. Remova o patch de segurança APSB25-08, limpe o cache, gere novamente o código e repita a solicitação da etapa 1 para confirmar se o tempo de execução retorna ao normal. (Opcional)

<u>Resultados esperados</u>:

O tempo de execução de `async/bulk` solicitações aumentou significativamente após a aplicação do patch de segurança.

<u>Resultados reais</u>:

O tempo de execução das solicitações `async/bulk` não deve ter aumentado significativamente após a aplicação do patch de segurança, embora seja esperado algum aumento no tempo.

## Solução

Para resolver o problema, aplique o [AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip).

## Como aplicar o patch

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

## Leitura relacionada

* [Atualização de segurança disponível para o Adobe Commerce - APSB25-08](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)
