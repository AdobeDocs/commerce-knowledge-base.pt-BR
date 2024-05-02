---
title: "ACSD-55334: rótulos não traduzidos por dicionários de tradução na resposta do GraphQL"
description: Aplique o patch ACSD-55334 para corrigir o problema do Adobe Commerce em que os rótulos não são traduzidos por dicionários de tradução na resposta do GraphQL.
feature: Categories, GraphQL
role: Admin, Developer
exl-id: c9d34a86-0c69-4fde-a46b-6583eff8b948
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-55334: rótulos não traduzidos por dicionários de tradução na resposta do GraphQL

O patch ASCD-55334 corrige o problema em que os rótulos não são traduzidos por dicionários de tradução na resposta do GraphQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.43 está instalado. A ID do patch é ASCD-55334. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os rótulos não são traduzidos por dicionários de tradução na resposta do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Instalar um pacote de idiomas.
1. Envie uma solicitação do GraphQL como:

   ```GrapQL
   query {
       products(filter: {}, pageSize: 25, sort: {}) {
           aggregations {
               label
           }
           total_count
       }
   }
   ```

1. Verifique a resposta.

<u>Resultados esperados</u>:

O rótulo *[!UICONTROL Category]* é traduzido.

<u>Resultados reais</u>:

O rótulo *[!UICONTROL Category]* não é traduzido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
