---
title: Alternar para o OpenSearch para Adobe Commerce na nuvem 2.4.4
promoted: true
description: O Adobe Commerce na infraestrutura em nuvem 2.4.4 não oferecerá suporte a versões do Elasticsearch após a 7.10. **Primeiro, é necessário atualizar para o Adobe Commerce 2.4.4 e, em seguida, mudar imediatamente do Elasticsearch para o OpenSearch 1.2.x.** O Adobe fornecerá instruções detalhadas mais próximas da versão 2.4.4 GA do Adobe Commerce.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Alternar para o OpenSearch para Adobe Commerce na nuvem 2.4.4

O Adobe Commerce na infraestrutura em nuvem 2.4.4 não oferecerá suporte a versões do Elasticsearch após a 7.10. **Você deve atualizar para o Adobe Commerce 2.4.4 primeiro e, em seguida, mudar imediatamente do Elasticsearch para o OpenSearch 1.2.x.** O Adobe fornecerá instruções detalhadas mais próximas da versão 2.4.4 GA do Adobe Commerce.

>[!NOTE]
>
>A alternância deve ser feita independentemente do provedor de nuvem.

O Adobe Commerce no local está adicionando suporte para o Elasticsearch 7.16 e OpenSearch 1.2 em todas as versões de patch de março de 2022 (2.4.4, 2.4.3-p2 e 2.3.7-p3). Na versão 2.4.4, o Adobe Commerce na infraestrutura em nuvem será transferido para o OpenSearch como mecanismo de pesquisa padrão, portanto, os comerciantes devem usar o OpenSearch no lugar do Elasticsearch antes de atualizar para o Adobe Commerce 2.4.4 ou posterior. Os comerciantes com implantações locais do Adobe Commerce podem usar o Elasticsearch ou o OpenSearch, pois o Adobe Commerce continuará a oferecer suporte a ambos.


## O que é o OpenSearch?

OpenSearch é uma bifurcação de Elasticsearch e Kibana. Ele é mantido pela AWS em vez do Elastic.co. Para saber mais, consulte GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Compatibilidade entre versões:**

**O Adobe Commerce na infraestrutura em nuvem será compatível com o Elasticsearch 7.10?**

**Sim** - a partir de meados de janeiro de 2022, o Adobe Commerce no cloud infrastructure versões 2.4.3-p1, 2.4.3-p2 e 2.3.7-p3 oferecerá suporte ao Elasticsearch 7.10.

Para o Adobe Commerce no local, a versão 7.16.x mais recente é recomendada para atenuar o Log4j.

## Migração:

## Quando os comerciantes podem migrar para o OpenSearch?

Após o Adobe Commerce 2.4.4.

Antes de começar o processo de atualização para o Adobe Commerce 2.4.4, no entanto, os comerciantes precisam estar em uma versão atual do Adobe Commerce que suporte o Elasticsearch 7.10 e estar em pelo menos Elasticsearch antes de começar o processo de atualização para o Adobe Commerce 2.4.4 ou para OpenSearch.

## O que os comerciantes (Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local) que não estão na versão 2.4.4 podem fazer? É possível atualizar para uma versão compatível do Elasticsearch (7.10, 7.16.1) ou para o OpenSearch? Eles precisam estar na versão mais recente compatível para fazer isso (como 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Se a versão principal do Adobe Commerce em que eles estão suportar o Elasticsearch 7.10, eles podem usá-lo.

Revisão [Requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) na documentação do desenvolvedor para compatibilidade de versões.

>[!NOTE]
>
>É recomendável planejar a atualização para o Adobe Commerce 2.4.4 o mais rápido possível, pois o Elasticsearch 7.10 será EOL em maio de 2022.

Os parceiros do Adobe podem se inscrever no nosso programa beta [aqui](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html) para obter acesso ao nosso código beta4 mais recente que foi testado em relação ao Elasticsearch 7.16.1 e OpenSearch 1.1.
