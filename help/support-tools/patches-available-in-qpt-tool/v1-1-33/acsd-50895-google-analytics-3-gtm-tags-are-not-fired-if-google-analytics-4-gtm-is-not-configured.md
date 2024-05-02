---
title: '"ACSD-50895: [!DNL Google Analytics] 3 tags GTM não são acionadas se [!DNL Google Analytics] 4 GTM não está configurado'''
description: Aplique o patch ACSD-50895 para corrigir o problema do Adobe Commerce em que [!DNL Google Analytics] 3 tags GTM não são acionadas se [!DNL Google Analytics] 4 GTM não está configurado.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 tags GTM não são acionadas se [!DNL Google Analytics] 4 GTM não está configurado

O patch ACSD-50895 corrige o problema em que [!DNL Google Analytics] 3 tags GTM não são acionadas se [!DNL Google Analytics] 4 GTM não está configurado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.33 está instalado. A ID do patch é ACSD-50895. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL Google Analytics] 3 tags GTM não são acionadas se [!DNL Google Analytics] 4 GTM não está configurado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como um usuário administrador.
1. Ativar **[!DNL Google Analytics 3]** e **[!DNL Google Tag Manager]** in **Admin** > **Loja** > **Configuração** > **Vendas** > **API do Google** > **Google Analytics**.
1. Não ative o **[!DNL Google Analytics 4]** e **[!DNL Google Tag Manager]**.
1. Abra a página do produto na Loja.

<u>Resultados esperados</u>:

As tags do GTM são acionadas somente quando **[!DNL Google Analytics]** 3 GTM está habilitado.

<u>Resultados reais</u>:

As tags do GTM não são acionadas quando **[!DNL Google Analytics]** 4 GTM está desativado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
