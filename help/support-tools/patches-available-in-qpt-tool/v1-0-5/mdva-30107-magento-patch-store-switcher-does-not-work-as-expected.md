---
title: 'MDVA-30107: o alternador de armazenamento não funciona como esperado'
description: O patch MDVA-30107 resolve o problema em que o alternador de loja não funciona como esperado se URLs de base diferentes forem usadas para visualizações de loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada.
exl-id: feaef9ed-615f-4a0a-a7c5-1833f993d27f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-30107: O alternador de armazenamento não funciona como esperado

O patch MDVA-30107 resolve o problema em que o alternador de loja não funciona como esperado se URLs de base diferentes forem usadas para visualizações de loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.0 - 2.3.5.x
* Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.3.5.x

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando um usuário alterna entre armazenamentos usando o alternador de armazenamento, a solicitação falha se o armazenamento de destino tiver um URL de base diferente.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois ou mais armazenamentos com URLs base diferentes.
1. Vá para uma página de categoria em uma vitrine de qualquer uma dessas lojas.
1. Tente alternar para a outra loja usando o alternador de loja.

<u>Resultados esperados</u>:

Você será redirecionado para uma página semelhante da outra loja.

<u>Resultados reais</u>:

Você é redirecionado para a página inicial da mesma loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
