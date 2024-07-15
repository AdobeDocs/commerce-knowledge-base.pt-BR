---
title: Solucionar problemas da página de criação de pedido no modo restrito [!UICONTROL CSP]
description: Este artigo explica os erros ao criar um pedido no lado do Administrador quando o modo restrito da CSP está Habilitado e fornece soluções para corrigir esses erros.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Solucionar problemas da página de criação de pedido no modo restrito [!UICONTROL CSP]

Este artigo fornece explicações e correções para os problemas do Adobe Commerce 2.4.7 ao criar uma ordem no lado do Administrador com **[!UICONTROL CSP restricted mode]** is *Enabled*, com o script &quot;*Recusado a executar o script integrado porque viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, Adobe Commerce no local e Magento Open Source:

* 2.4.7
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - A página **criar pedido** do administrador está corrompida ou não pode ser carregada

A página de ordem de criação **do administrador** está corrompida ou não pode ser carregada, com o script embutido &quot;*Recusado a executar porque viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Criar um novo pedido.

<u>Resultados esperados</u>:

A página **criar ordem** do administrador é carregada normalmente.

<u>Resultados reais</u>:

A página Admin **criar ordem** está em branco ou sem componentes. O seguinte erro [!DNL JS] é exibido no log do console do navegador: &quot;*Recusou-se a executar o script embutido porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, o **[!UICONTROL CSP]** é configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas.
O cabeçalho **[!UICONTROL CSP]** correspondente não contém a palavra-chave `unsafe-inline` dentro da diretiva `script-src` para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts por causa de [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para corrigir esse problema, você deve</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) os scripts bloqueados usando a classe `SecureHtmlRenderer`.
1. Use a classe `CSPNonceProvider` para permitir que scripts sejam executados.
Adobe Commerce e Magento Open Source 2.4.7 e posterior incluem um provedor **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar a geração de cadeias de caracteres [!DNL nonce] exclusivas para cada solicitação. Essas cadeias de caracteres [!DNL nonce] são anexadas ao cabeçalho [!UICONTROL CSP].

   Use a função `generateNonce` em `Magento\Csp\Helper\CspNonceProvider` para obter uma cadeia de caracteres [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Adicione um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao arquivo `csp_whitelist.xml` do módulo.

## Problema - O método de pagamento está ausente ou não está funcionando

O método de pagamento está ausente ou não está funcionando na **página de criação de pedido** do Administrador, com o script embutido &quot;*Recusado para executar porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Criar um novo pedido.
1. Crie um novo cliente.
1. Informe os detalhes do cliente.
1. Informe os detalhes do pedido (produtos, método de entrega).
1. Selecione um método de pagamento.

<u>Resultados esperados</u>:

Você pode selecionar um método de pagamento e prosseguir para colocar um pedido com sucesso.

<u>Resultados reais</u>:

O método de pagamento está ausente ou não está funcionando. O seguinte erro [!DNL JS] é exibido no log do console do navegador: &quot;*Recusou-se a executar o script embutido porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: &quot;script-src ...*&quot;.

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, o **[!UICONTROL CSP]** é configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas.
O cabeçalho **[!UICONTROL CSP]** correspondente não contém a palavra-chave `unsafe-inline` dentro da diretiva `script-src` para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts por causa de **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para corrigir esse problema, você deve</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) os scripts bloqueados usando a classe `SecureHtmlRenderer`.
1. Use a classe `CSPNonceProvider` para permitir que scripts sejam executados.
Adobe Commerce e Magento Open Source 2.4.7 e posterior incluem um provedor **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar a geração de cadeias de caracteres [!DNL nonce] exclusivas para cada solicitação. Essas cadeias de caracteres [!DNL nonce] são anexadas ao cabeçalho [!UICONTROL CSP].

   Use a função `generateNonce` em `Magento\Csp\Helper\CspNonceProvider` para obter uma cadeia de caracteres [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [adicione um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao arquivo `csp_whitelist.xml` do módulo.

## Problema - O administrador não pode fazer um pedido

Um administrador não pode enviar um pedido na **página Criar pedido** do Administrador, com o script embutido &quot;*Recusado a executar, pois ele viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Criar um novo pedido.
1. Crie um novo cliente.
1. Informe os detalhes do cliente.
1. Informe os detalhes do pedido (produtos, método de entrega).
1. Selecione um método de pagamento.
1. Enviar o pedido.

<u>Resultados esperados</u>:

Você pode enviar um pedido com sucesso.

<u>Resultados reais</u>:

Você não pode enviar um pedido. O seguinte erro [!DNL JS] é exibido no log do console do navegador: &quot;*Recusou-se a executar o script embutido porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, o **[!UICONTROL CSP]** é configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas.
O cabeçalho **[!UICONTROL CSP]** correspondente não contém a palavra-chave `unsafe-inline` dentro da diretiva `script-src` para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts por causa de **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Para corrigir esse problema, você deve</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) os scripts bloqueados usando a classe `SecureHtmlRenderer`.
1. Use a classe `CSPNonceProvider` para permitir que scripts sejam executados.
Adobe Commerce e Magento Open Source 2.4.7 e posterior incluem um provedor **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar a geração de cadeias de caracteres [!DNL nonce] exclusivas para cada solicitação. Essas cadeias de caracteres [!DNL nonce] são anexadas ao cabeçalho [!UICONTROL CSP].

   Use a função `generateNonce` em `Magento\Csp\Helper\CspNonceProvider` para obter uma cadeia de caracteres [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Adicione um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao arquivo `csp_whitelist.xml` do módulo.
