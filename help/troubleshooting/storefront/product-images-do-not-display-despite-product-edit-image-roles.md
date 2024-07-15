---
title: As imagens do produto não são exibidas apesar das funções de imagem Edição de produto
description: Este artigo fornece uma correção para quando as imagens do produto não são exibidas em sua loja, apesar das funções de imagem definidas na página Edição do produto.
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# As imagens do produto não são exibidas apesar das funções de imagem Edição de produto

Este artigo fornece uma correção para quando as imagens do produto não são exibidas em sua loja, apesar das funções de imagem definidas na página Edição do produto.

**Causa:** em instâncias do Adobe Commerce com mais de um armazenamento, algumas imagens de produtos podem ter os valores `no_selection` para os atributos de função de imagem `image`, `small_image`, `thumbnail`, `swatch`. Esses `no_selection` valores surgem quando a função da imagem do produto é definida no escopo global de todas as lojas em vez do escopo de uma determinada loja (em outras palavras, em **Todas as Exibições de Loja** em vez de uma **Exibição de Loja** específica). Para entender se esse é o seu caso, execute o script SQL da seção **Causa** abaixo.

**Solução:** exclua linhas com os valores `no_selection` dessas imagens usando o script SQL da seção Solução abaixo.

## Versões afetadas

* Adobe Commerce no local 2.X.X
* Adobe Commerce na infraestrutura em nuvem 2.X.X

## Problema

As imagens do produto podem não ser exibidas na loja, embora as funções de imagem (Base, Pequeno, Miniatura, Amostra) tenham sido definidas corretamente na página Produto do painel do Administrador.

Ao verificar a página Produto com a **Exibição da Imagem** definida como **Todas as exibições da loja**, a imagem terá as funções definidas na tela **Detalhes da Imagem**.

![todos_os_modos_de_exibição.png](assets/all_store_views.png)

![funções_de_imagem.png](assets/image_roles.png)

No entanto, na loja, a imagem não é exibida; ao verificar a página Produto no nível de loja específico (alternando a **Exibição da Loja**), a imagem está lá, mas as funções não estão definidas.

![image_roles_not_set.png](assets/image_roles_not_set.png)

## Causa

Nas instâncias do Adobe Commerce de várias lojas (com mais de uma loja), algumas imagens de produtos podem ter os valores `no_selection` para os atributos `image`, `small_image`, `thumbnail`, `swatch` (esses atributos correspondem às funções de imagem). Esses `no_selection` valores surgem quando a função da imagem do produto é definida no escopo global de todas as lojas em vez do escopo de uma determinada loja (em outras palavras, em **Todas as Exibições de Loja** em vez de uma **Exibição de Loja** específica).

Tecnicamente falando: em `store_id=0` (que contém as configurações globais para todas as lojas na sua instância do Adobe Commerce), as funções de imagem do produto podem ser definidas: isso significa que os atributos `image`, `small_image`, `thumbnail`, `swatch` têm valores válidos (caminho para imagens). Ao mesmo tempo, em `store_id=1` (que é uma representação de armazenamento específica), os valores desses atributos são `no_selection`.

### Como verificar se esse é o seu problema

Executar esta consulta SQL:

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Se a consulta retornar um resultado como abaixo, você está lidando com o problema documentado neste artigo:

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### Por que isso acontece?

Se o aplicativo Adobe Commerce tiver mais de um armazenamento, talvez ele não sincronize os dados entre um determinado armazenamento e as configurações de armazenamento Global.

Os valores em `store_id=1` têm mais prioridade que o armazenamento padrão (global) (`store_id=0`). Assim, o aplicativo pode ignorar as configurações globais de imagem e usar a configuração de escopo de armazenamento (`no_selection` para atributos de função de imagem) ao exibir uma imagem.

## Solução {#solution}

Excluir atributos com os valores `no_selection` usando este script SQL:

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Após a remoção desses atributos, as funções para armazenamentos específicos são definidas e as imagens são exibidas na loja.

## Detalhes adicionais

Você não poderá ver os resultados da correção imediatamente se o Cache de página cheia estiver ativado na instância do Adobe Commerce.

Para que as alterações sejam exibidas, atualize o cache de páginas usando o menu **Gerenciamento de cache** do seu painel de Administração.

## Mais informações

### Armazenamentos e escopos

[Lojas e escopos de armazenamento](/docs/commerce-admin/stores-sales/site-store/stores.html) em nosso guia do usuário

### Imagens

[Carregando imagens do produto](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) no guia do usuário

### Cache

* [Gerenciamento de cache](/docs/commerce-admin/systems/tools/cache-management.html) em nosso Guia do Sistema do Administrador do usuário.
* [Gerenciar o cache](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) na documentação do desenvolvedor