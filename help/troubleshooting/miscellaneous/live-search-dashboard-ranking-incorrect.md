---
title: A classificação do painel e do resultado da pesquisa [!DNL Live Search] está incorreta
description: Este artigo fornece informações sobre solução de problemas se os dados no painel do [!DNL Live Search] estiverem incorretos ou se a classificação dos resultados da pesquisa não for a esperada.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# A classificação do painel e do resultado da pesquisa [!DNL Live Search] está incorreta

Se você perceber que os dados exibidos no painel [!DNL Live Search] estão incorretos, ou se a [classificação dos resultados da pesquisa](https://experienceleague.adobe.com/pt-br/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) não é o que você espera, veja os seguintes motivos:

* O campo `topLevelSku` do contexto de produto em `productView` eventos está ausente. Isso causa conversões vazias e outras métricas inesperadas.

* O evento `add-to-cart` não tem o campo `productContext` definido e preenchido.

* Tipo de ambiente incorreto. Por exemplo, se o ambiente estiver definido como *[!UICONTROL Testing]* em vez de *[!UICONTROL Production]*. Consulte [Contexto da vitrine](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) para obter mais informações.

* O contexto de resultados da pesquisa está ausente do evento [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
