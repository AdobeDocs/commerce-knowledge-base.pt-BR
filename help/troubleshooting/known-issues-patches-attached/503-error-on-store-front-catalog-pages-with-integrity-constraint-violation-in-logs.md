---
title: Erro 503 nas páginas do catálogo principal da loja com "Violação de restrição de integridade" nos logs
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.0 relacionado às páginas do catálogo principal da loja que estão inacessíveis.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Erro 503 nas páginas do catálogo principal da loja com &quot;Violação de restrição de integridade&quot; nos logs

>[!NOTE]
>
>Este artigo fornece uma correção como solução alternativa, mas o problema foi permanentemente corrigido no Adobe Commerce na infraestrutura em nuvem versão v2.3.3 e é recomendável atualizar para a v2.3.3. Siga as etapas em [Atualizar versão do Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html) na documentação do desenvolvedor.

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura de nuvem 2.2.0 relacionado à inacessibilidade das páginas do catálogo principal da loja, com a mensagem de erro semelhante à seguinte no log: *Violação de restrição de integridade: 1062 Entrada duplicada &#39;%entry%&#39; para a chave &#39;PRIMARY&#39;, a consulta era: INSERT INTO \`search\_tmp\_%number%*.

## Problema

As páginas do catálogo principal da loja ficam inacessíveis inesperadamente. O log de erros tem uma descrição de erro semelhante à seguinte: *Violação de restrição de integridade: 1062 Entrada duplicada &#39;%entry%&#39; para a chave &#39;PRIMARY&#39;, a consulta era: INSERT INTO \`search\_tmp\_%number%*.

O problema está relacionado à pesquisa e é causado pela existência do índice desatualizado junto com o novo após o reindexação.

## Solução

Para corrigir o problema, você precisa remover índices desatualizados do Elasticsearch e aplicar o patch para evitar que eles apareçam.

Para listar todos os índices, use o seguinte comando:

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indices</pre>

Para remover os índices desatualizados, localize-os no banco de dados e use o seguinte comando:

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Exemplo:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Correção

Os patches estão anexados a este artigo. Para baixar um patch, role até o final do artigo e clique no nome de arquivo necessário ou clique em um dos links a seguir:

[Baixar MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[Baixar MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Versões compatíveis do Adobe Commerce

Os patches foram criados para as seguintes edições e versões:

* Adobe Commerce na infraestrutura em nuvem 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce na infraestrutura em nuvem 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

O patch `MDVA-9590_EE_2.2.0_COMPOSER_v2` também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3
* Adobe Commerce no local 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3

O patch `MDVA-13203_EE_2.2.4_V1_COMPOSER` também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3
* Adobe Commerce no local 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Links úteis

* [Local dos arquivos de log para a arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem](/help/how-to/general/log-locations-directories-for-starter-plan.md) em nossa base de dados de conhecimento de suporte.
* [Local dos arquivos de log para a arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) em nossa base de dados de conhecimento de suporte.
* [Local dos arquivos de log do Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) na documentação do desenvolvedor.

## Arquivos Anexados
