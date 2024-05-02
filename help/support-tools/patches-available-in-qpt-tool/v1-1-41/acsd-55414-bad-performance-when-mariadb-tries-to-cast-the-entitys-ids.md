---
title: "ACSD-55414: mau desempenho quando MariaDB tenta lançar os entitys_ids"
description: Aplique o patch ACSD-55414 para corrigir o problema do Adobe Commerce quando o MariaDB tenta converter "entitys_ids" de sequência de caracteres em número inteiro, isso dificulta o desempenho da reindexação.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414: Mau desempenho quando MariaDB tenta lançar o `entitys_ids`

O patch ACSD-55414 corrige o problema em que o desempenho da reindexação é dificultado quando o MariaDB tenta converter `entitys_ids` da sequência de caracteres ao número inteiro. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.41 está instalado. A ID do patch é ACSD-55414. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desempenho da reindexação é dificultado quando o MariaDB tenta lançar o `entitys_ids` da sequência de caracteres ao número inteiro.

<u>Etapas a serem reproduzidas</u>:

1. Atualizar `setup/performance-toolkit/profiles/ce/small.xml` configurando *50000* produtos simples.
1. Gere este perfil executando o comando: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Executar reindexação: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Resultados esperados</u>:

O reindexação leva um tempo razoável para ser concluída.

<u>Resultados reais</u>:

A reindexação leva muito tempo para ser concluída.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
