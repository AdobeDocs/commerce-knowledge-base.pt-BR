---
title: Solucionar problemas da página de check-out da loja no modo restrito [!UICONTROL CSP]
description: Este artigo explica os erros que você pode experimentar ao visualizar a página de check-out no modo restrito do CSP e fornece soluções para corrigir esses erros.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Solucionar problemas da página de check-out da loja no modo restrito [!UICONTROL CSP]

Este artigo fornece explicações e correções para os problemas do Adobe Commerce 2.4.7 ao visualizar a página de check-out em **[!UICONTROL CSP restricted mode]**, com o script &quot;*Recusado a executar em linha porque viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, Adobe Commerce no local e Magento Open Source:

* 2.4.7
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - A página de finalização da loja está quebrada ou não consegue carregar

A página **check-out da loja** foi desfeita ou não pode ser carregada, com o script embutido &quot;*Recusado a executar porque viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
1. Adicione um produto ao carrinho e prossiga para a finalização.

<u>Resultados esperados</u>:

A página de check-out é totalmente carregada normalmente.

<u>Resultados reais</u>:

A página de check-out está em branco ou não contém componentes. O seguinte erro [!DNL JS] é exibido no log do console do navegador: &quot;*Recusou-se a executar o script embutido porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, o **[!UICONTROL CSP]** é configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas.
O cabeçalho **[!UICONTROL CSP]** correspondente não contém a palavra-chave `unsafe-inline` dentro da diretiva `script-src` para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts por causa de **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

O método de pagamento está ausente ou não está funcionando na página **check-out da loja**, com o script &quot;*Recusado para executar script embutido porque viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
2. Adicione um produto ao carrinho e prossiga para a finalização.
3. Selecione um método de pagamento.

<u>Resultados esperados</u>:

Você pode selecionar um método de pagamento e prosseguir para colocar um pedido com sucesso.

<u>Resultados reais</u>:

O método de pagamento está ausente ou não está funcionando. O seguinte erro [!DNL JS] é exibido no log do console do navegador: &quot;*Recusou-se a executar o script embutido porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, o **[!UICONTROL CSP]** é configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas.
O cabeçalho **[!UICONTROL CSP]** correspondente não contém a palavra-chave `unsafe-inline` dentro da diretiva `script-src` para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts por causa de **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

## Problema - o cliente não pode fazer um pedido

Um cliente não pode fazer um pedido com o script integrado &quot;*Recusado a executar porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: mensagem de erro &quot;script-src ...*&quot; no log de console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
2. Adicione um produto ao carrinho e prossiga para a finalização.
3. Selecione um método de pagamento.
4. Clique em **Fazer pedido**.

<u>Resultados esperados</u>:

Você pode fazer um pedido com sucesso.

<u>Resultados reais</u>:

Você não pode fazer um pedido. O seguinte erro [!DNL JS] é exibido no log do console do navegador: &quot;*Recusou-se a executar o script embutido porque ele viola a seguinte diretiva de Política de Segurança de Conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, o **[!UICONTROL CSP]** é configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas.
O cabeçalho **[!UICONTROL CSP]** correspondente não contém a palavra-chave `unsafe-inline` dentro da diretiva `script-src` para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts por causa de **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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
