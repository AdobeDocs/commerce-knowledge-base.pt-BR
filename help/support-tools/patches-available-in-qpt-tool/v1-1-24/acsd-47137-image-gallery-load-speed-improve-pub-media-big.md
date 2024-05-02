---
title: '"ACSD-47137: melhorar a velocidade de carregamento da galeria de imagens na pasta "pub/media" big"'
description: Aplique o patch ACSD-47137 para melhorar a velocidade de carregamento da galeria de imagens quando a pasta "pub/media" for muito grande.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137: melhore a velocidade de carregamento da galeria de imagens quando `pub/media` pasta grande

O patch ACSD-47137 melhora a velocidade de carregamento da galeria de imagens quando o `pub/media` a pasta é muito grande. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-47137. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A velocidade de carregamento da galeria de imagens é lenta quando a variável `pub/media` a pasta é muito grande.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador do Adobe Commerce > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** para _Não_.
1. Limpe o cache de configuração.
1. Saia e faça logon como usuário administrador novamente.
1. Na barra lateral Admin, acesse **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e selecione a categoria raiz.
1. Expanda a **[!UICONTROL Content]** e clique em **[!UICONTROL Select from Gallery]**.

Ao carregar a página, o Adobe Commerce envia `media_gallery/directories/gettree` solicitação para carregar a árvore de pastas de mídia.

<u>Resultados esperados</u>:

A variável `media_gallery/directories/gettree` a solicitação deve carregar o conteúdo somente dos diretórios necessários, sem ser fazer o loop de toda a lista de caminhos do `pub/media/` pasta.

<u>Resultados reais</u>:

A variável `media_gallery/directories/gettree` demora muito para carregar quando a variável `pub/media/` tem muito conteúdo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
