---
title: '"Alterações incompatíveis com versões anteriores para [!DNL GraphQL] &grave;placeOrder" [!DNL API] in Adobe Commerce 2.4.6-p8"'
promoted: true
description: Este artigo fornece um patch para a versão conhecida do Adobe Commerce 2.4.6-p8 Cloud e problema no local em que "placeOrder" [!DNL GraphQL API] não retorna uma resposta de erro esperada, como visto nas versões anteriores do patch 2.4.6. Isso pode levar a uma experiência de check-out interrompida para comerciantes que usam vitrine PWA ou qualquer outra vitrine baseada no  [!DNL GraphQL API] para suas lojas.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Alterações incompatíveis com versões anteriores para [!DNL GraphQL] `placeOrder` [!DNL API] no Adobe Commerce 2.4.6-p8

Este artigo fornece um patch para a versão conhecida do Adobe Commerce 2.4.6-p8 Problema na nuvem e no local, em que o `placeOrder` [!DNL GraphQL API] não retorna uma resposta de erro esperada, como visto nas versões anteriores do patch 2.4.6. Isso pode levar a uma experiência de check-out interrompida para comerciantes que usam a loja [!DNL PWA] ou qualquer outra loja baseada em [!DNL GraphQL API] para suas lojas.

>[!NOTE]
>
>Entre em contato com os Serviços de suporte se encontrar problemas ao aplicar o patch.

## Produtos e versões afetados

* Adobe Commerce na nuvem 2.4.6-p8
* Adobe Commerce no local 2.4.6-p8

## Problema

Após a atualização no patch somente de segurança do Adobe Commerce 2.4.6-p8, o [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) não retorna uma resposta de erro esperada, como visto em qualquer versão anterior do patch 2.4.6. Isso pode levar a uma experiência de check-out interrompida para comerciantes que usam a loja [!DNL PWA] ou qualquer outra loja baseada em [!DNL GraphQL API] para suas lojas.

<u>Etapa de reprodução</u>:

Execute a solicitação `placeOrder` [!DNL GraphQL] onde você espera uma resposta de erro.

<u>Resultado esperado</u>:

Você recebeu uma resposta de erro esperada.

<u>Resultado real</u>:

Em vez de uma resposta de erro esperada, você recebe uma resposta bem-sucedida, mas com uma nova chave `errors` com esta aparência:

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Solução para software Adobe Commerce na nuvem e Adobe Commerce no local

Para resolver o problema, aplique o patch.
Para baixá-lo, clique no link a seguir:

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Como aplicar o patch

Descompacte o arquivo e consulte [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

## Somente para comerciantes do Adobe Commerce na nuvem - Como saber se os patches foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, talvez você queira verificar se o patch foi aplicado com sucesso.

<u>Você pode fazer isso seguindo as etapas abaixo, usando o arquivo de exemplo `VULN-27015-2.4.7_COMPOSER.patch` **como exemplo</u>**:

1. [Instalar o [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Executar o comando:<br>
   ![ac-13283-tell-if-patch-plied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Você deve ver uma saída semelhante a esta, onde VULN-27015 retorna o status *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

