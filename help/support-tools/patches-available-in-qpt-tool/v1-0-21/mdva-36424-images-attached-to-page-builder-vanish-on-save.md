---
title: "MDVA-36424: as imagens anexadas ao construtor de página desaparecem ao salvar"
description: O patch MDVA-36424 resolve o problema em que as imagens anexadas aos elementos do page builder desaparecem quando a categoria é salva pela segunda vez no caso de vários sites, com o URL base do site padrão sendo diferente do URL do administrador. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36424. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424: as imagens anexadas ao construtor de página desaparecem ao salvar

O patch MDVA-36424 resolve o problema em que as imagens anexadas aos elementos do page builder desaparecem quando a categoria é salva pela segunda vez no caso de vários sites, com o URL base do site padrão sendo diferente do URL do administrador. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.21 está instalado. A ID do patch é MDVA-36424. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Magento:**

Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens de mídia anexadas aos elementos do page builder não são salvas se o URL base de backend for diferente do URL base da loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie um segundo site - site2.
1. Defina um URL base diferente para o site 2 (o URL base usado no administrador deve ser diferente do segundo site).
1. Definir o segundo site como site padrão (**Lojas** > *Configurações* > **Todas as lojas** > Selecione o segundo site > definir como *Padrão*).
1. Navegue até a página de categorias no back-end e vá para uma visualização de edição de categoria.
1. Navegue até **Conteúdo** > *Descrição*.
1. Adicione uma coluna ao conteúdo e defina uma imagem de fundo usando a galeria de mídia.
1. Salve a categoria.
1. Vá para a **Conteúdo** > *Descrição* novamente; você verá a imagem salva corretamente.
1. Salve a categoria novamente.
1. Vá para a **Conteúdo** > *Descrição*.

<u>Resultados esperados</u>:

A imagem não é removida ao salvar a categoria.

<u>Resultados reais</u>:

A imagem é removida depois de salvar a categoria uma segunda vez.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
