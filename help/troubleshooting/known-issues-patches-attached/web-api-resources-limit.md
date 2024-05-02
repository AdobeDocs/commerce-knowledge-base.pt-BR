---
title: A API da Web não pode processar solicitações com mais de 20 itens na matriz
description: Este artigo fornece uma solução para o problema em que a API da Web não consegue processar uma mensagem que contém mais de 20 itens na matriz do Adobe Commerce 2.4.3.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# A API da Web não pode processar solicitações com mais de 20 itens na matriz

Este artigo fornece uma solução para o problema em que a API da Web não consegue processar uma mensagem que contém mais de 20 itens na matriz do Adobe Commerce 2.4.3.

## Produtos e versões afetados:

* Adobe Commerce (todos os métodos de implantação) 2.4.3 e 2.3.7-p1
* Magento Open Source 2.4.3 e 2.3.7-p1

## Problema

A API da Web não pode processar a mensagem (por exemplo, Atualização do Stock) que contém mais de 20 itens na matriz.

## Causa

No Adobe Commerce 2.4.3, a limitação de taxa integrada foi adicionada às APIs de Magento para impedir ataques de negação de serviço (DoS).

Por padrão, a seguinte limitação de taxa de API integrada está disponível:

* As solicitações REST que contêm entradas que representam uma lista de entidades estão limitadas a um máximo padrão de 20 entidades
* As consultas REST e GraphQL que permitem resultados paginados são limitadas a um máximo padrão de 300 itens por página

## Solução

Para desativar os limites de entrada na solicitação da API REST, aplique um dos seguintes patches (dependendo da versão):

* [MC-43048_set_rate_limits_2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048_set_rate_limits_2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Versões compatíveis do Adobe Commerce

Os patches foram criados para:

* Adobe Commerce na infraestrutura em nuvem 2.4.3 e 2.3.7-p1
* Adobe Commerce no local 2.4.3 e 2.3.7-p1

Os patches não são compatíveis com outras versões do Adobe Commerce.

### Como aplicar o patch

Descompacte o baixado `.zip` e aplique o patch conforme descrito em [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

>[!WARNING]
>
>Se você suspeitar que seu armazenamento está enfrentando um ataque de DoS, a Adobe recomenda reduzir os limites de entrada padrão para um valor menor para impor restrições ao número de recursos que podem ser solicitados.  É possível personalizar os limites padrão de forma programática usando o [argumentos do construtor de classe](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)
>conforme descrito em nossa documentação do desenvolvedor: [Segurança da API > Limitação de taxa > Máximo de entradas de parâmetro](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Leitura relacionada

[Segurança da API > Limitação de taxa](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) na documentação do desenvolvedor.
