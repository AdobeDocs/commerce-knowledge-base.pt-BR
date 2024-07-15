---
title: "MDVA-36832: Imagens duplicadas em páginas com largura de exibição de 768px"
description: O patch MDVA-36832 corrige o problema em que as imagens são duplicadas em páginas com largura de visualização de 768px. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 está instalada. A ID do patch é MDVA-36832. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832: Imagens duplicadas em páginas com largura de exibição de 768px

O patch MDVA-36832 corrige o problema em que as imagens são duplicadas em páginas com largura de visualização de 768px. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 está instalada. A ID do patch é MDVA-36832. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce local e Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens são duplicadas em páginas com largura de exibição de 768px.

<u>Etapas a serem reproduzidas:</u>

1. Vá para backend > CONTEÚDO > Páginas e edite qualquer página.
1. Adicione qualquer imagem à página.
1. Ir para o front-end e abrir a página editada.
1. Abra as ferramentas do desenvolvedor no Chrome.
1. Ative &quot;device view&quot; e selecione iPad view ou defina a largura da página como 768px.

<u>Resultado real:</u>

A imagem é duplicada.

<u>Resultado esperado:</u>

Somente uma imagem adicionada deve estar visível na página.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
