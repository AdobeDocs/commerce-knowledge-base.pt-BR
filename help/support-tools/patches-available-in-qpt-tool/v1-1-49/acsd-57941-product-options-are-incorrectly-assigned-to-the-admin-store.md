---
title: 'ACSD-57941: as opções de produto são atribuídas incorretamente à loja do administrador'
description: Aplique o patch ACSD-57941 para corrigir o problema do Adobe Commerce em que as opções do produto são atribuídas incorretamente à loja do administrador em vez de suas respectivas lojas.
feature: Products
role: Admin, Developer
exl-id: 7aa6f5c0-b718-4c3a-be0f-d86ae15e31a2
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-57941: as opções de produto são atribuídas incorretamente à loja do administrador

O patch ACSD-57941 corrige o problema em que as opções do produto são atribuídas incorretamente à loja do administrador em vez de suas respectivas lojas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 está instalado. A ID do patch é ACSD-57941. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As opções de produto são atribuídas incorretamente à loja do administrador em vez de suas respectivas lojas.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Importe o mesmo produto com algumas opções personalizadas.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e abra o produto criado. Clique em **[!UICONTROL Customizable options]** e verifique se as opções importadas estão visíveis.
1. Importe o mesmo arquivo mais algumas vezes.

<u>Resultados esperados</u>:

As opções personalizadas são atualizadas.

<u>Resultados reais</u>:

As opções personalizadas do produto são duplicadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
