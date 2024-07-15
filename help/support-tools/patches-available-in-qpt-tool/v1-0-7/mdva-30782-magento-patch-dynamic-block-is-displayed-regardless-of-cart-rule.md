---
title: "MDVA-30782: o bloco dinâmico é exibido independentemente da regra do carrinho"
description: O patch MDVA-30782 corrige o problema em que um bloco dinâmico é exibido independentemente da regra do carrinho. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: o bloco dinâmico é exibido independentemente da regra do carrinho

O patch MDVA-30782 corrige o problema em que um bloco dinâmico é exibido independentemente da regra do carrinho. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O bloco dinâmico é exibido na página mesmo quando a condição da regra de preço de catálogo relacionada não é atendida.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos.
1. Crie uma regra de preço de catálogo aplicável somente a um desses produtos.
1. Crie um bloco dinâmico e atribua a ele a regra de preço de catálogo recém-criada.
1. Crie um widget com os seguintes parâmetros:
   * Tipo = Rotador dinâmico de blocos
   * Blocos dinâmicos a serem exibidos = Blocos dinâmicos especificados
   * Especificar Blocos dinâmicos = bloquear a partir da etapa \#3Layout Atualizações (pode ser qualquer)
   * Exibir em = Todos os Tipos de Produto
   * Contêiner = Informações auxiliares do produto
1. Execute a reindexação e limpe o cache.
1. Verificar se há etapa de formulário de bloco dinâmico nas duas páginas de produto \#3

<u>Resultados esperados</u>:

O bloco dinâmico é exibido somente na primeira página do produto.

<u>Resultados reais</u>:

O bloco dinâmico é exibido em ambas as páginas de produto. Com Blocos dinâmicos a serem exibidos = Regra de preço de catálogo relacionada na etapa \#3, o resultado é o mesmo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
