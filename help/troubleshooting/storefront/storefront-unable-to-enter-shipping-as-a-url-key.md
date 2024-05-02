---
title: Não é possível salvar "delivery" como chave de URL
description: Este artigo fornece uma solução alternativa para o problema quando você não consegue salvar "envio" como uma chave de URL (por exemplo, "/envio") para produtos ou páginas de CMS. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Não é possível salvar &quot;delivery&quot; como chave de URL

Este artigo fornece uma solução alternativa para o problema quando você não consegue salvar &quot;envio&quot; como uma chave de URL (por exemplo, &quot;/envio&quot;) para produtos ou páginas de CMS. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.x

## Problema

Não é possível salvar uma página CMS com o termo &quot;envio&quot; na chave do URL.

<u>Etapas a serem reproduzidas</u>:

Crie uma página CMS com a chave de URL como &quot;envio&quot;.

<u>Resultado esperado</u>:

A página é salva com &quot;envio&quot; na chave do URL.

<u>Resultado real</u>:

Não é possível salvar e um erro é exibido: *O valor especificado no campo Chave de URL geraria uma URL que já existe.*

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

Não é possível usar o termo &quot;envio&quot; na chave do URL; no entanto, você pode usar o termo &quot;envio&quot; combinado com outra letra ou número (por exemplo, &quot;envio1&quot; e &quot;envio2&quot;). Embora o termo não precise ser &quot;envio&quot;+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - o termo pode ser qualquer cadeia de caracteres, desde que o comprimento não exceda 255 caracteres.

Execute as seguintes etapas:

1. Faça logon no Administrador do Commerce.
1. Ir para **Marketing** > SEO E Pesquisa > **Substituições de URL**.
1. Clique em **Adicionar regravação de URL**.
1. Selecionar *Personalizado* na lista suspensa Criar regravação de URL.
   1. Digite o Caminho da solicitação &quot;envio&quot;. Observação: o Caminho da solicitação é o que um usuário insere no navegador e o Caminho do destino é para onde ele deve ser redirecionado.
   1. Digite no Caminho do público alvo a nova chave do URL (por exemplo, &quot;shipping1&quot;).
   1. Selecionar **Não** no menu suspenso Redirecionar.

## Leitura relacionada

* [Substituições de URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) em nosso guia do usuário.
* [Práticas recomendadas da SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) em nosso guia do usuário.
