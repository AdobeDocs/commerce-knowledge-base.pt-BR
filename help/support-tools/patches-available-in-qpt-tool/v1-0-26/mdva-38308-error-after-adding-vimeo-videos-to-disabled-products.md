---
title: "MDVA-38308: Erro ao adicionar vídeos do Vimeo a produtos desativados"
description: 'O patch de qualidade MDVA-38308 para Adobe Commerce resolve o problema em que os usuários recebem a mensagem de erro: *Aviso: Índice indefinido: extensão em /lib/internal/Magento/Framework/File/Uploader.php na linha 806,* ao adicionar vídeos Vimeo a produtos desativados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalada. A ID do patch é MDVA-38308. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.'
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: Erro ao adicionar vídeos Vimeo a produtos desabilitados

O patch de qualidade MDVA-38308 para Adobe Commerce resolve o problema em que os usuários recebem a mensagem de erro: *Aviso: índice indefinido: extensão em /lib/internal/Magento/Framework/File/Uploader.php na linha 806,* ao adicionar vídeos do Vimeo a produtos desativados. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.26 está instalado. A ID do patch é MDVA-38308. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.4.1-p1, 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao adicionar vídeos do Vimeo a produtos desativados, você recebe a seguinte mensagem de erro:  *Aviso: índice indefinido: extensão em /lib/internal/Magento/Framework/File/Uploader.php na linha 806*

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Desative o produto criado.
1. Tente adicionar um vídeo do Vimeo ao produto desativado.

<u>Resultados esperados</u>:

O vídeo é adicionado sem erros.

<u>Resultados reais</u>:

Você recebe o seguinte erro:
*Aviso: índice indefinido: extensão em /lib/internal/Magento/Framework/File/Uploader.php na linha 806*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Leitura relacionada

Para saber mais sobre a Ferramenta de correções de qualidade em nossa base de conhecimento de suporte, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção em nossa base de conhecimento de suporte.
