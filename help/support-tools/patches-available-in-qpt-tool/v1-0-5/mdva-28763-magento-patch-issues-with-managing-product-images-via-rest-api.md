---
title: "MDVA-28763: problemas com o gerenciamento de imagens de produtos por meio da API REST"
description: O patch MDVA-28763 resolve vários problemas relacionados ao gerenciamento da galeria de mídia usando a API REST. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. Os problemas estão programados para serem corrigidos em versões posteriores do Adobe Commerce.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: problemas com o gerenciamento de imagens de produtos por meio da API REST

O patch MDVA-28763 resolve vários problemas relacionados ao gerenciamento da galeria de mídia usando a API REST. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. Os problemas estão agendados para serem corrigidos em versões posteriores do Adobe Commerce (consulte as descrições de problemas em [Problemas](#issues).

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce no local 2.3.2 - 2.3.3.x
* Adobe Commerce na infraestrutura em nuvem 2.3.2 - 2.3.3.x

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problemas {#issues}

O patch MDVA-28763 inclui correções para os seguintes problemas associados à galeria de mídia:

* Ao usar a API REST para atualizar vídeos do YouTube (`PUT rest/V1/products/ {SKU}`), o Adobe Commerce exibe uma miniatura do vídeo, mas o reprodutor de vídeo não é carregado quando você clica no botão &quot;Reproduzir&quot;. Agendado para ser corrigido no Adobe Commerce 2.3.6.
* A chamada `PUT /V1/products/:sku/media/:entryId` cria uma nova entrada em vez de substituir a existente. Corrigido no Adobe Commerce 2.3.5.
* Problemas com a exclusão de imagens de produtos quando os produtos são atribuídos a várias exibições de loja. Corrigido no Adobe Commerce 2.3.4.
* Os comerciantes com vários sites agora podem usar o REST para criar e atualizar produtos, preservando a herança das funções de imagem e imagem. Anteriormente, quando um comerciante usava o REST para criar e atualizar produtos e um produto era atualizado para exibição de loja, as funções de imagem padrão eram carregadas e salvas para essa exibição de loja. Como resultado, as funções de imagem de exibição de loja pararam de herdar do escopo padrão após a atualização. Agendado para ser corrigido no Adobe Commerce 2.3.6.
* Atributos de mídia (imagem, miniatura etc.) os valores em exibições de armazenamento que fazem referência a imagens removidas não são limpos automaticamente. Agendado para ser corrigido no Adobe Commerce 2.4.2.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
