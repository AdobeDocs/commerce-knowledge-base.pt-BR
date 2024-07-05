---
title: Não é possível salvar o envio como uma chave de URL
description: Este artigo fornece uma solução alternativa para o problema quando você não consegue salvar o envio como uma chave de URL (_e.g., /shipping_) para produtos ou páginas CMS. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Não é possível salvar _envio_ como uma chave de URL

Este artigo fornece uma solução alternativa para o problema quando você não consegue salvar o delivery como uma chave de URL (_por exemplo, /delivery_) para produtos ou páginas CMS. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.x

## Problema

Não é possível salvar uma página CMS com o termo _envio_ na chave URL.

<u>Etapas a serem reproduzidas</u>:

Criar um **[!UICONTROL CMS page]** com a chave do URL como _envio_.

<u>Resultado esperado</u>:

A página é salva com _envio_ como a chave do URL.

<u>Resultado real</u>:

Não é possível salvar porque este erro ocorre:
*O valor especificado no campo Chave de URL geraria uma URL que já existe.*

## Causa

A remessa é uma palavra reservada definida em `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Solução

Não é possível usar o termo _envio_ na chave do URL - no entanto, você pode usar o termo _envio_ combinado com outra letra ou número (_Por exemplo, envio1 e envio2_).

Embora o termo não tenha de ser _envio_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - o termo pode ser qualquer sequência de caracteres, desde que o comprimento não exceda *255* caracteres.

## Execute as seguintes etapas:

1. Faça logon no Administrador do Adobe Commerce.
1. Ir para **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Clique em **[!UICONTROL Add URL Rewrite]**.
1. Selecionar **[!UICONTROL Custom]** no **[!UICONTROL Create URL Rewrite]** menu suspenso.
   1. Digite o [!UICONTROL Request Path] as **_envio_**.
   1. No **[!UICONTROL Target Path]**, digite a nova chave do URL (_Por exemplo, &quot;delivery1&quot;_).
   1. Selecionar **[!UICONTROL No]** no **[!UICONTROL Redirect]** menu suspenso.


      (**Nota**: o Caminho da solicitação é o que um usuário insere no navegador e o Caminho do destino é para onde ele deve ser redirecionado.)

Além disso, evite usar essas palavras-chave rotuladas como *reservado* palavras-chave que fazem com que apareça a mesma exceção. Usar qualquer uma dessas palavras-chave listadas abaixo como um valor de chave de URL causará a exibição do mesmo erro.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Leitura relacionada

* [Substituições de URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) em nosso Guia do usuário de merchandising e promoções.
* [Práticas recomendadas da SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) em nosso Guia do usuário de merchandising e promoções.
