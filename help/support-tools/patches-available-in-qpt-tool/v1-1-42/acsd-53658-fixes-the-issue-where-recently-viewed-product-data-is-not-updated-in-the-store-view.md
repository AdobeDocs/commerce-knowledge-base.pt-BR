---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** dados não atualizados corretamente na exibição do armazenamento'
description: Aplique o patch ACSD-53658 para corrigir o problema do Adobe Commerce em que os dados **[!UICONTROL Recently Viewed Product]** não são atualizados corretamente na exibição da loja.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** dados não atualizados corretamente na exibição do armazenamento

O patch ACSD-53658 corrige o problema em que os dados de **[!UICONTROL Recently Viewed Product]** não são atualizados corretamente na exibição do armazenamento. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. A ID do patch é ACSD-53658. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os dados **[!UICONTROL Recently Viewed Product]** não são atualizados corretamente na exibição de armazenamento.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Painel de administração.
1. Crie uma segunda exibição de loja para o site padrão.
1. Crie um produto simples.
1. Defina um nome de produto diferente para a nova visualização de loja.
1. Crie um widget **[!UICONTROL Recently Viewed Product]**.
1. Configure este widget para ser exibido na Página inicial.
1. Abra a página do produto na Loja a partir da exibição padrão da loja.
1. Abra a Home page.
1. Ao usar o alternador de loja, alterne para a segunda exibição de loja.

<u>Resultados esperados</u>:

O nome do produto é atualizado no widget.

<u>Resultados reais</u>:

O nome do produto não é atualizado no widget.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
