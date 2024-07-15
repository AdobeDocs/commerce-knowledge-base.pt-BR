---
title: 'MDVA-43983: Produtos definidos como "Não Visível Individualmente" aparecem nos resultados da pesquisa'
description: O patch MDVA-43983 resolve o problema em que os produtos definidos como "Não visível individualmente" ainda aparecem nos resultados da pesquisa avançada do catálogo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-43983. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983: Produtos definidos como &quot;Não visível individualmente&quot; aparecem nos resultados da pesquisa

O patch MDVA-43983 resolve o problema em que os produtos definidos como &quot;Não visível individualmente&quot; ainda aparecem nos resultados da pesquisa avançada do catálogo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-43983. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos definidos como &quot;Não visível individualmente&quot; ainda aparecem nos resultados da pesquisa avançada do catálogo.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo com **Tipo de Entrada de Catálogo para o Proprietário da Loja** como **Suspenso** ou **Amostra Visual** (por exemplo, Cor).
1. Defina **Usar na Pesquisa** como **Sim** e **Visível na Pesquisa Avançada** como **Sim**.
1. Adicione algumas opções de atributo.
1. Crie produtos com **Visibilidade** como **Não visível individualmente**.
1. Atribuir opções de atributo de cor.
1. Vá para a página **Pesquisa avançada de catálogo** na vitrine.
1. Selecione somente a opção Atributo de cor no campo Atributo de cor e deixe o restante dos campos em branco ou como estão.
1. Envie um formulário de pesquisa avançada.
1. Observe os resultados da pesquisa.

<u>Resultados esperados</u>:

Os produtos definidos como &quot;Não visível individualmente&quot; não aparecem nos resultados da pesquisa avançada do catálogo.

<u>Resultados reais</u>:

Os produtos definidos como &quot;Não visível individualmente&quot; aparecem nos resultados da pesquisa avançada do catálogo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
