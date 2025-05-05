---
title: 'ACSD-51528: comportamentos diferentes na formatação de snake_case'
description: Aplique o patch ACSD-51528 para corrigir o problema do Adobe Commerce em que há comportamentos diferentes na formatação de snake_case.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: comportamentos diferentes na formatação de snake_case

O patch ACSD-51528 corrige comportamentos diferentes na formatação de snake_case. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-51528. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os diferentes comportamentos na formatação de snake_case.

<u>Etapas a serem reproduzidas</u>:

1. Teste a função `\Magento\Framework\Api\DataObjectHelper::populateWithArray` com uma variedade de nomes de propriedades diferentes.
1. As propriedades com nomes como *NewPName* devem ser transformadas em *new_p_name*, em vez disso, estão sendo transformadas em *new_pname*.
1. Além disso, ao usar a função *getNewPName* no objeto, *null* será retornado porque o *Abstract model* transformará corretamente a chamada para *new_p_name*, tornando ambas as funções incompatíveis entre si.

<u>Resultados esperados</u>

A função **[!UICONTROL populateWithArray]** deve transformar as propriedades de objeto em snake_case corretamente, tornando-a compatível com **[!DNL AbstractModel's]** `Getters` e `Setters`.

<u>Resultados reais</u>

Ao usar a função **[!UICONTROL populateWithArray]**, qualquer propriedade de objeto que contenha duas ou mais letras maiúsculas em uma linha em seu nome fará com que a transformação snake_case fique incorreta na matriz de dados final.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
