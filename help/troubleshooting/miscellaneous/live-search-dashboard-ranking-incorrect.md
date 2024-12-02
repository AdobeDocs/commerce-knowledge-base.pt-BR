---
title: A classificação do painel e do resultado da pesquisa [!DNL Live Search] está incorreta
description: Este artigo fornece informações sobre solução de problemas se os dados no painel  [!DNL Live Search]  estiverem incorretos ou se a classificação dos resultados da pesquisa não for o esperado.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# A classificação do painel e do resultado da pesquisa [!DNL Live Search] está incorreta

Se você perceber que os dados exibidos no painel [!DNL Live Search] estão incorretos, ou se a [classificação dos resultados da pesquisa](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) não é o que você espera, veja os seguintes motivos:

* O campo `topLevelSku` do contexto de produto em `productView` eventos está ausente. Isso causa conversões vazias e outras métricas inesperadas.

* O evento `add-to-cart` não tem o campo `productContext` definido e preenchido.

* Tipo de ambiente incorreto. Por exemplo, se o ambiente estiver definido como *[!UICONTROL Testing]* em vez de *[!UICONTROL Production]*. Consulte [Contexto da vitrine](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) para obter mais informações.

* O contexto de resultados da pesquisa está ausente do evento [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
