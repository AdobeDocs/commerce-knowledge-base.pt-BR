---
title: Solução de problemas do módulo [!UICONTROL Product Recommendations] no Adobe Commerce
description: Este artigo fala sobre sugestões de solução de problemas para o módulo [!UICONTROL Product Recommendations] no Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: af9ee28c5819a9d1b97411210816bfe8a9522614
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Solução de problemas do módulo [!UICONTROL Product Recommendations] no Adobe Commerce

Este artigo aborda sugestões para a solução de problemas do

```php
magento/product-recommendations
```

módulo e sua dependência

```php
saas-export
```

módulo, pois você precisa que ambos os módulos operem para usar a ferramenta [!UICONTROL Product Recommendations] no Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce 2.4.4 - 2.4.7

## Solução de problemas do módulo de recomendações de produtos

Se você tiver configurado o

```php
magento/product-recommendations
```

módulo corretamente, (Verifique [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) em nossa documentação do desenvolvedor.) mas você não estiver vendo nenhuma recomendação, tente o seguinte:

* É possível que o módulo não tenha tido tempo suficiente para coletar dados comportamentais. Deixe o sistema em execução por 24 horas para que ele possa começar a coletar dados. Considere a implantação de um tipo de recomendação que não exija dados comportamentais, como &quot;*Mais itens semelhantes*&quot;.

* Se você não estiver vendo as recomendações configuradas, é possível que ainda não haja dados suficientes para criar recomendações para o usuário.

* Verifique se o Espaço de Dados [!DNL SaaS] ou a Chave [!DNL API] são válidos. Se você receber um erro depois de especificar seu Espaço de Dados [!DNL SaaS] ou sua chave [!DNL API] durante a inicialização das recomendações do produto, verifique se inseriu corretamente o [[!DNL SaaS] Espaço de Dados e a [!DNL API] chave](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) (em nosso guia do usuário). Para garantir que as chaves [!DNL MageID] e [!DNL API] estejam vinculadas, o usuário que possui o [!DNL MageID], normalmente o usuário que possui a licença do Adobe Commerce, precisa ser o mesmo usuário que gera a chave [!DNL API]. Se precisar alterar o [!DNL MageID] que foi usado, [envie um tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Se [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (em nosso guia de usuário) estiver *habilitado*, a Adobe Commerce não coletará dados comportamentais até que o comprador dê o seu consentimento. Se **[!UICONTROL Cookie Restriction Mode]**estiver *desabilitado*, o Adobe Commerce coletará dados comportamentais por padrão.

## Módulo de exportação do catálogo [!DNL SaaS]

Para problemas relacionados à Exportação do Catálogo [!DNL SaaS] (

```php
saas-export
```

) módulo:

1. Confirme se os trabalhos do [[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (na documentação do desenvolvedor) estão em execução.
1. Confirme se o [[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) (na documentação do desenvolvedor) está em execução e se    ```php    Product Feed    ```    [!UICONTROL indexer] está definido como    ```php    Update by Schedule    ```    .
1. Confirme se os módulos estão *habilitados*. A variável    ```php    saas-export    ```    o metapackage instala os seguintes módulos, que devem ser *habilitados*:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Verifique os [logs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) (na documentação do desenvolvedor). Verifique se não há erros associados aos módulos acima.
1. Atualize o [!UICONTROL Configuration cache]. Vá para **Sistema** > **Ferramentas** > **Gerenciamento de Cache** e limpe o [!UICONTROL Configuration cache].
1. Confirme se há dados na tabela do banco de dados `cde_products_products_feed`.

   >[!NOTE]
   >
   >Se você não puder encontrar essa tabela, verifique a tabela `catalog_data_exporter_products`. O nome da tabela foi alterado na versão 103.3.0 do [!DNL Data Export].

## Eventos

[Verificar coleção de eventos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify), em nossa documentação de desenvolvedor, descreve os eventos comportamentais enviados para a Adobe Commerce.

## Leitura relacionada

* [Desenvolvimento de administradores do Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview) em nossa documentação de desenvolvedor
* [Introdução ao Recommendations de produto](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) no Guia do Recommendations de produto
* [Criar Recommendations de Produtos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create) no Guia do Recommendations de Produtos
* [Revisar logs e solucionar problemas](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) no Guia de Exportação de Dados do [!DNL SaaS]
* [[!DNL SaaS] Notas de Versão da Extensão de Exportação de Dados](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) no Guia de Exportação de Dados Adobe Commerce para Serviços [!DNL SaaS]
