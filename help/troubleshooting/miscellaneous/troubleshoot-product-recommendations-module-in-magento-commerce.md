---
title: Solução de problemas do módulo Recommendations do produto no Adobe Commerce
description: Este artigo aborda sugestões para a solução de problemas do
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Solução de problemas do módulo Recommendations do produto no Adobe Commerce

Este artigo aborda sugestões para a solução de problemas do

```php
magento/product-recommendations
```

módulo e sua dependência

```php
saas-export
```

como você precisa que ambos os módulos funcionem para usar a ferramenta Recommendations do produto no Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce 2.4.4 - 2.4.7

## Solução de problemas do módulo de recomendações de produtos

Se você tiver configurado o

```php
magento/product-recommendations
```

módulo corretamente (Verifique o [Product Recommendations - Instalar e Configurar o Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) na documentação do desenvolvedor.), mas se você não estiver vendo nenhuma recomendação, tente o seguinte:

* É possível que o módulo não tenha tido tempo suficiente para coletar dados comportamentais. Deixe o sistema em execução por 24 horas para que ele possa começar a coletar dados. Considere a implantação de um tipo de recomendação que não exija dados comportamentais, como &quot;Mais artigos como este&quot;.

* Se você não estiver vendo as recomendações configuradas, é possível que ainda não haja dados suficientes para criar recomendações para o usuário.

* Verifique se o espaço de dados SaaS ou a chave da API são válidos. Se você receber um erro depois de especificar seu Espaço de dados SaaS ou sua chave de API durante a inicialização das recomendações do produto, verifique se inseriu corretamente o [Espaço de dados SaaS e a chave de API](https://docs.magento.com/user-guide/configuration/services/saas.html) (em nosso guia do usuário). Para garantir que a MageID e a chave da API estejam vinculadas, o usuário proprietário da MageID, normalmente o usuário proprietário da licença do Adobe Commerce, precisa ser o mesmo usuário que gera a chave da API. Se precisar alterar a MageID que foi usada, [envie um tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Se o [Modo de restrição de cookies](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) (em nosso guia do usuário) estiver habilitado, a Adobe Commerce não coletará dados comportamentais até que o comprador dê o seu consentimento. Se o Modo de restrição de cookie estiver desativado, o Adobe Commerce coletará dados comportamentais por padrão.

## Módulo de exportação de SaaS do catálogo

Para problemas relacionados à exportação de SaaS do catálogo (

```php
saas-export
```

) módulo:

1. Confirme se os trabalhos do [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (na documentação do desenvolvedor) estão em execução.
1. Confirme se os [indexadores](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (na documentação do desenvolvedor) estão em execução e se    ```php    Product Feed    ```    indexador está definido como    ```php    Update by Schedule    ```    .
1. Confirme se os módulos estão ativados. A variável    ```php    saas-export    ```    o metappackage instala os seguintes módulos, que devem ser habilitados:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Verifique os [logs](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (na documentação do desenvolvedor). Verifique se não há erros associados aos módulos acima.
1. Atualizar cache de configuração. Vá para **Sistema** > **Ferramentas** > **Gerenciamento de Cache** e limpe o cache de configuração.
1. Confirme se há dados na    ```php    catalog_data_exporter_products    ```    tabela de banco de dados.

## Eventos

[Eventos de recomendação](https://devdocs.magento.com/recommendations/verify.html), em nossa documentação para desenvolvedores, descreve os eventos comportamentais enviados para a Adobe Commerce.

## Leitura relacionada

* [Recommendations de produtos - Visão geral](https://devdocs.magento.com/recommendations/product-recs.html) em nossa documentação do desenvolvedor
* [Recommendations de produtos - Instalar e configurar o Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) na documentação do desenvolvedor
* [Marketing - Recommendations de produto](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) no nosso guia do usuário
* [Criar Recommendations de Produto](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) em nosso guia do usuário
