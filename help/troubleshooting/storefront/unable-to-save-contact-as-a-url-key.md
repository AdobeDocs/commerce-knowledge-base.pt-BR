---
title: Não é possível salvar *contact* como chave de URL
description: Este artigo fornece uma solução alternativa para o problema quando você não consegue salvar *contato* como uma chave de URL (por exemplo, "/contact") para produtos ou páginas do CMS. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Não é possível salvar *contato* como a chave da URL

Este artigo fornece uma solução alternativa para o problema quando você não pode salvar *contato* como uma chave de URL (por exemplo, &quot;/contact&quot;) para produtos ou páginas do CMS.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.x

## Problema

Não é possível salvar um produto ou uma página do CMS usando o termo *contato* como chave de URL. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.

<u>Etapas a serem reproduzidas</u>:

Crie uma página do CMS com *contato* como a chave da URL.

<u>Resultado esperado</u>:

A página é salva com *contato* como a chave da URL.

<u>Resultado real</u>:

Não é possível salvar a página. Você recebe o erro: *O valor especificado no campo Chave de URL geraria uma URL que já existe.*

## Causa

*Contato* é uma palavra reservada definida em `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Solução

Você não pode usar o termo *contato* como sua chave de URL, mas pode usar o termo *contato* combinado com outra letra ou número (por exemplo, *contato1* e *contato2*). Embora o termo não precise ser *contact+\&lt;outro número ou letra\>*, o termo pode ser qualquer cadeia de caracteres, desde que o comprimento não exceda 255 caracteres.

Execute as seguintes etapas:

1. Faça logon no Commerce Admin.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Clique em **[!UICONTROL Add URL Rewrite]**.
1. Selecione *[!UICONTROL Custom]* no menu suspenso [!UICONTROL Create URL Rewrite].
   1. Em [!UICONTROL Request Path], digite &quot;contato&quot;. Observe que o [!UICONTROL Request Path] é o que um usuário insere no navegador e o [!UICONTROL Target Path] é para onde ele deve ser redirecionado.
   1. Em [!UICONTROL Target Path], digite a nova chave de URL (por exemplo, &quot;contact1&quot;).
   1. Selecione *[!UICONTROL No]* no menu suspenso [!UICONTROL Redirect].

## Leitura relacionada

* [Substituições de URL](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) em nosso guia do usuário.
* [Práticas recomendadas da SEO](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/marketing/seo/seo-overview) em nosso guia do usuário.
