---
title: "MDVA-36833: paginação quebrada na página de resultados da pesquisa"
description: O patch MDVA-36833 corrige o problema em que a paginação é interrompida quando o catálogo compartilhado é ativado e alguns produtos são excluídos do catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalada. A ID do patch é MDVA-36833. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: paginação quebrada na página de resultados da pesquisa

O patch MDVA-36833 corrige o problema em que a paginação é interrompida quando o catálogo compartilhado é ativado e alguns produtos são excluídos do catálogo compartilhado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalada. A ID do patch é MDVA-36833. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce (todos os métodos de implantação) 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exclusão de alguns produtos do catálogo compartilhado resulta em falha na paginação dos resultados da pesquisa.

<u>Etapas a serem reproduzidas:</u>

1. Habilitar Catálogo compartilhado.
1. Vá para **Catálogo** > **Catálogos Compartilhados** e configure o Catálogo Compartilhado padrão atribuindo todos os produtos a ele.
1. Carregue a vitrine e procure por &quot;jaqueta&quot;.
1. Observe os produtos listados na primeira página. Deve haver 12 produtos.
1. Anote 11 SKUs na primeira página. Vá para o back-end e carregue o Catálogo compartilhado padrão.
1. Cancele a atribuição dos SKUs anotados anteriormente no Catálogo compartilhado padrão.
1. Vá até a loja e procure por &quot;jaqueta&quot;.
1. Verifique a primeira página dos resultados da pesquisa.

<u>Resultado real:</u>

A primeira página tem um produto e o restante dos produtos está disponível na segunda página.

<u>Resultado esperado:</u>

A primeira página deve ter 12 produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.


## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
