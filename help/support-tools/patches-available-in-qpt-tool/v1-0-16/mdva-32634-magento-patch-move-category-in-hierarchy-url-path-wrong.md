---
title: "Patch MDVA-32634: mover categoria na hierarquia url_path errado"
description: O patch MDVA-32634 resolve o problema em que o url\_path da categoria do catálogo não é alterado após mover a categoria na hierarquia. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Correção MDVA-32634: mover categoria na hierarquia url_path errado

O patch MDVA-32634 resolve o problema em que o url\_path da categoria do catálogo não é alterado após mover a categoria na hierarquia. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.1 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Mover uma categoria de catálogo na hierarquia resulta em um url\_path incorreto. O url\_path da categoria atribuída ao escopo de armazenamento padrão \[ **id:0** \] permanece inalterado após mover a categoria na hierarquia.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce. Crie a seguinte estrutura de categoria na categoria raiz: move-cat sub-move-cat sub-move-cat2 new-cat-move
1. Verifique a categoria \[ url\_path \] atributo \[ id: 120 \] para atribuição de valor na tabela \[ catalog\_category\_entity\_varchar \] usando a seguinte consulta:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Ele deve fornecer o seguinte resultado:

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Os valores \[ url\_path \] foram gerados e atribuídos a Todo o escopo do armazenamento \[ 0 \]. Isso está correto ao comparar com uma instância sem B2B.
1. Vá para a lista de categorias de back-end, arraste \[ move-cat \] e solte-a em \[ new-cat-move \]. Agora a categoria deve se parecer com: new-cat-move-cat sub-move-cat sub-move-cat2
1. Verifique a tabela \[ catalog\_category\_entity\_varchar \] usando a seguinte query:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Resultados esperados</u>:

O url\_path atribuído a todo o escopo de armazenamento \[ 0 \] também deve ser atualizado com o novo caminho.

<u>Resultados reais</u>:

O url\_path atribuído a todo o escopo de armazenamento \[ 0 \] permanece inalterado, mesmo que não haja esse caminho disponível após a movimentação. Além disso, ela tem novos valores url\_path criados para cada armazenamento.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
