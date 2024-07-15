---
title: "MDVA-36615: resultados incorretos do filtro de grade de produtos de catálogo"
description: O patch MDVA-36615 corrige o problema com a contagem de produtos incorreta na grade de produtos de administração. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36615. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 7ed70753-c637-4c13-8290-aa5e8a4d1b65
feature: Catalog Management, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36615: resultados incorretos do filtro de grade de produtos de catálogo

O patch MDVA-36615 corrige o problema com a contagem de produtos incorreta na grade de produtos de administração. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36615. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Contagem de produtos incorreta na grade de produtos de administração.

<u>Etapas a serem reproduzidas:</u>

1. Crie produtos simples e configuráveis com a mesma frase no nome (por exemplo, &quot;red shirt&quot; / &quot;red shirt xs&quot;).
1. Na barra lateral *Admin*, vá para **Catálogo** > **Produtos** > e pesquise essa frase.
1. Clique em **Filtros**. Defina o Tipo como *Produto Configurável*.
1. Clique em **Aplicar Filtros**.

<u>Resultado real:</u>

Número correto no contador de produto correspondente.

<u>Resultado esperado:</u>

Número incorreto no contador de produto correspondente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
