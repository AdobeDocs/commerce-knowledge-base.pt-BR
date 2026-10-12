---
title: Não é possível salvar *contact* como chave de URL
description: Este artigo fornece uma solução alternativa para o problema quando você não consegue salvar *contato* como uma chave de URL (por exemplo, "/contact") para produtos ou páginas do CMS. Ao tentar salvar a chave do URL, você recebe um erro que indica que a chave do URL é um URL duplicado.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '350'
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
