---
title: '"ACSD-53583: Melhore o desempenho do reindex parcial para [!UICONTROL Category Products] e [!UICONTROL Product Categories] indexadores'''
description: Aplique o patch ACSD-53585 para melhorar o desempenho parcial do reindexação para indexadores de Produtos de categoria e Categorias de produto.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: Melhore o desempenho da reindexação parcial para indexadores de Produtos de categoria e Categorias de produto

O patch ACSD-53583 melhora o desempenho do reindexação parcial de *Categoria Produtos* e *Categorias de produto* indexadores. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.39 está instalado. A ID do patch é ACSD-53583. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3
* Não compatível com [!DNL Live Search] módulo. Para aplicar este patch a [!DNL Live Search] instalação, solicite um patch ACSD-55719 adicional.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação parcial leva mais tempo do que a reindexação completa.

<u>Etapas a serem reproduzidas</u>:

1. Ativar todos os indexadores para *Atualização por Agendamento*.
1. Gerar dados com o [!DNL Performance Toolkit] (perfil médio).
1. Faça alterações em todos os produtos e categorias para que eles estejam no backlog de índice e todos os índices estejam ociosos.
1. Executar reindexação parcial para *Categoria Produtos* e *Categorias de produto* indexadores.

<u>Resultados esperados</u>:

A reindexação parcial é chamada uma vez por produto e leva quase o mesmo tempo que a reindexação completa, pois todos os produtos e categorias foram alterados.

<u>Resultados reais</u>:

A reindexação parcial é chamada muitas vezes por produto e leva mais tempo do que a reindexação completa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
