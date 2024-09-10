---
title: "ACSD-58790: corrige a funcionalidade de pinçar para zoom nas imagens da página de detalhes do produto na exibição móvel no [!DNL Chrome]"
description: ACSD-58790 corrige o problema do Adobe Commerce em que a imagem na exibição móvel em  [!DNL Chrome]  não dava zoom na imagem conforme esperado.
feature: Storefront
role: Admin, Developer
source-git-commit: 51c740dc70937c7b80d8492d02ee4a758f103a35
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-58790: corrige a funcionalidade de pinçar para zoom nas imagens da página de detalhes do produto na exibição móvel no [!DNL Chrome]

O patch ACSD-58790 corrige o problema do Adobe Commerce em que a imagem na exibição móvel em [!DNL Chrome] não dava zoom na imagem conforme esperado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-58790. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige a funcionalidade de pinçar para zoom nas imagens da página de detalhes do produto na exibição móvel no [!DNL Chrome].

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com uma imagem.
1. Abra o produto em um navegador [!DNL Chrome].
1. Clique na imagem e verifique se ela dá zoom de clique duplo.
1. Alterne para a exibição móvel usando as ferramentas de desenvolvedor do [!DNL Chrome].
1. Clique na imagem.
1. Toque duas vezes.

<u>Resultados esperados</u>:

A imagem é ampliada ao clicar duas vezes.

<u>Resultados reais</u>:

A imagem não amplia quando clica duas vezes. Este problema é específico do [!DNL Chrome] no modo de exibição móvel, pois a funcionalidade de zoom funciona conforme esperado no [!DNL Firefox].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
