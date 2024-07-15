---
title: "MDVA-34695: produtos e categorias não são exibidos"
description: O patch MDVA-34695 resolve o problema em que os produtos e categorias não são exibidos na grade de categorias no Admin. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é MDVA-34695. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: Produtos e categorias não são exibidos

O patch MDVA-34695 resolve o problema em que os produtos e categorias não são exibidos na grade de categorias no Admin. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalada. A ID do patch é MDVA-34695. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0-2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Valores negativos para `children_count` aparecem no banco de dados após a exclusão de categorias.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no back-end do Administrador.
1. Navegue até **Catálogo > Categorias**.
1. Clique em **Adicionar subcategoria**.
1. Defina o **nome da categoria** = *Pai 1* e salve.
1. Clique em **Adicionar subcategoria**.
1. Defina **nome da categoria** = *Filho 1* e salve.
1. Clique em **Adicionar subcategoria**.
1. Defina **nome da categoria** = *Filho 2* e salve.
1. Clique em **Adicionar subcategoria**.
1. Defina **nome da categoria** = *Filho 3* e salve. Neste ponto, esta categoria deve ter um nível = *5*.
1. Clique na categoria **Filho 1**.
1. Exclua a categoria.

<u>Resultados esperados</u>:

A grade de categorias mostra os produtos e as categorias, conforme esperado.

<u>Resultados reais</u>:

A grade de categorias está vazia. Verifique a tabela `catalog_category_entity` no banco de dados. Observe que `children_count` se tornou negativo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
