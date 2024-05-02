---
title: 'MDVA-35092: Erro do Vimeo: "Vídeo não encontrado"'
description: 'O patch MDVA-35092 corrige o problema em que você vê Erro: *"Vídeo não encontrado"*. Essa mensagem de erro é exibida ao inserir um vídeo do Vimeo usando a interface nativa Adicionar vídeo no administrador de produto do Adobe Commerce. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: Erro do Vimeo: &quot;Vídeo não encontrado&quot;

O patch MDVA-35092 corrige o problema em que você vê Erro: *&quot;Vídeo não encontrado&quot;*. Essa mensagem de erro é exibida ao inserir um vídeo do Vimeo usando a interface nativa Adicionar vídeo no administrador de produto do Adobe Commerce. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.17 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.5 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A API simples do Vimeo para de funcionar conforme esperado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador.
1. Para editar um produto existente, vá para **CATÁLOGO** > **Produtos** > **Editar**, ou para criar um novo produto, vá para **CATÁLOGO** > **Produtos** > **Editar** > **Adicionar produto**.
1. Clique em **Imagens E Vídeos** na página Produto.
1. Clique em **Adicionar vídeo** e adicione o URL de um vídeo do Vimeo. Clique em **Salvar**.

<u>Resultados esperados</u>:

O novo vídeo é encontrado e salvo.

<u>Resultados reais</u>:

Erro: *&quot;Vídeo não encontrado&quot;* é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
