---
title: "MDVA-36853: Não há carregamento de imagens de grandes galerias de mídia"
description: O patch MDVA-36853 corrige o problema de quando nenhuma imagem é carregada, pois o widget galeria de mídia do construtor de páginas não é carregado quando você tem um diretório de mídia grande.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: Não há carregamento de imagens de grandes galerias de mídia

O patch MDVA-36853 corrige o problema de quando nenhuma imagem é carregada, pois o widget galeria de mídia do construtor de páginas não é carregado quando você tem um diretório de mídia grande.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalada. A ID do patch é MDVA-36853. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce local e Adobe Commerce na infraestrutura em nuvem 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Defina **Habilitar Galeria de Mídia Antiga** = *Sim* em **Admin > Lojas > Configuração > Avançado > Sistema > Galeria de Mídia**.
1. Navegue até **Conteúdo > Blocos** e crie um novo bloco CMS ou edite um bloco CMS existente.
1. Clique no botão **Editar com Pagebuilder**.
1. Adicione um elemento de mídia.
1. Clique no botão **Selecionar da Galeria**.

<u>Resultados esperados</u>:

O widget galeria de mídia e as imagens da galeria de mídia são carregados, conforme esperado.

<u>Resultados reais</u>:

O widget de galeria de mídia e as imagens da galeria de mídia não são carregados quando você tem um diretório `pub/media/catalog/product/cache/` grande.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
