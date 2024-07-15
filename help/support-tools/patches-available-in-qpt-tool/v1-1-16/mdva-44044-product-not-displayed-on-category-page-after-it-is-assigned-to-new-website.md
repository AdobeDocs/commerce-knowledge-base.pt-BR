---
title: "MDVA-44044: o produto não é exibido na página de categoria depois de ser atribuído ao novo site"
description: O patch MDVA-44044 resolve o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalada. A ID do patch é MDVA-44044. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: e3a179ed-243c-4200-a01a-796657bd31ab
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-44044: produto não exibido na página de categoria depois de atribuído ao novo site

O patch MDVA-44044 resolve o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalada. A ID do patch é MDVA-44044. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto não é exibido na página de categoria depois de ser atribuído a um novo site.

<u>Etapas a serem reproduzidas</u>:

1. Defina o modo do indexador para o agendamento.
1. Crie um modo de exibição de site, loja e loja secundário.
1. Adicionar um código de armazenamento secundário em `index.php`:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Crie uma nova categoria.
1. Crie um novo produto atribuído à categoria recém-criada. Certifique-se de atribuí-lo somente ao site principal.
1. Execute o cron.
1. Abra a categoria na loja.
1. Atribua o produto ao site secundário.
1. Execute o cron novamente.

<u>Resultados esperados</u>:

O produto é exibido na página da categoria após um indexador agendado.

<u>Resultados reais</u>:

O produto não é exibido na página de categoria até que uma reindexação completa seja feita.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
