---
title: "ACSD-58375: a chave de API do YouTube configurada incorretamente causa erro ao adicionar vídeo no nível de exibição da loja"
description: Aplique o patch ACSD-58375 para corrigir o problema do Adobe Commerce em que uma configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de exibição da loja.
feature: Catalog Management, Configuration
role: Admin, Developer
source-git-commit: 1887a74b0c5545f9213f54602c58de7028d1ad72
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-58735: a chave de API do YouTube configurada incorretamente causa erro ao adicionar vídeo no nível de exibição da loja

O patch ACSD-58735 corrige o problema em que uma configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de exibição da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 está instalado. A ID do patch é ACSD-58735. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de visualização da loja.

<u>Etapas a serem reproduzidas</u>:

1. Vá para Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Alterar o *Escopo* para o nível *[!UICONTROL Main Website]*.
1. Adicione a chave da API do YouTube.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Selecione qualquer produto e navegue até *[!UICONTROL Images and Video]*. Clique em **[!UICONTROL Add Video]**.
1. Copie um link de vídeo do YouTube e cole-o no campo de link do vídeo. Saia do campo.

<u>Resultados esperados</u>:

A chave de API do YouTube tem um escopo global e está oculta no nível do site.

<u>Resultados reais</u>:

O seguinte erro é lançado: *O vídeo não é mostrado devido ao seguinte motivo: a chave de API não é válida. Passe uma chave de API válida*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
