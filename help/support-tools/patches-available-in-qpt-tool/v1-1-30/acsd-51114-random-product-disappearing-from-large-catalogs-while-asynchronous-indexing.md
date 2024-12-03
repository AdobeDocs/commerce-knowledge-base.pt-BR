---
title: 'ACSD-51114: produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada'
description: Aplique o patch ACSD-51114 para corrigir o problema do Adobe Commerce Os produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada

>[!NOTE]
>
>Este patch está obsoleto.

O patch ACSD-51114 corrige o problema de produtos aleatórios que desapareciam de catálogos grandes quando a indexação assíncrona estava ativada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. A ID do patch é ACSD-51114. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]:página Procurar patches].Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada.

<u>Etapas a serem reproduzidas</u>:

1. Crie um conjunto de 10 produtos.
1. Defina todos os indexadores para o modo **[!UICONTROL Update on Save]**.
1. Crie uma categoria e atribua todos os produtos a ela.
1. Desative todos os produtos.
1. Abra a categoria e verifique se não há produtos lá.
1. Defina todos os indexadores para o modo **[!UICONTROL Update on Schedule]**.
1. Defina o `DEFAULT_BATCH_SIZE` como 2 em `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Ativar produtos na seguinte ordem: 1º, 9º, 2º, 5º, 10º, 3º.
1. Execute o comando cron.
1. Abra a categoria novamente.

<u>Resultados esperados</u>:

Todos os produtos ativados são exibidos.

<u>Resultados reais</u>:

Nem todos os produtos habilitados são mostrados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
