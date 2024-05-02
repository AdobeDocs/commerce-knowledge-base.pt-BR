---
title: Solução de problemas da página de check-out da loja em [!UICONTROL CSP] modo restrito
description: Este artigo explica os erros que você pode experimentar ao visualizar a página de check-out no modo restrito do CSP e fornece soluções para corrigir esses erros.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Solução de problemas da página de check-out da loja em [!UICONTROL CSP] modo restrito

Este artigo fornece explicações e correções para problemas do Adobe Commerce 2.4.7 ao visualizar a página de check-out no **[!UICONTROL CSP restricted mode]**, com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, Adobe Commerce no local e Magento Open Source:

* 2.4.7
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - A página de finalização da loja está quebrada ou não consegue carregar

A variável **checkout da loja** A página está quebrada ou não consegue carregar, com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
1. Adicione um produto ao carrinho e prossiga para a finalização.

<u>Resultados esperados</u>:

A página de check-out é totalmente carregada normalmente.

<u>Resultados reais</u>:

A página de check-out está em branco ou não contém componentes. As seguintes [!DNL JS] o erro é exibido no log do console do navegador: &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, **[!UICONTROL CSP]** está configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração e no `report-only` para todas as outras páginas.
Os correspondentes **[!UICONTROL CSP]** o cabeçalho não contém a variável `unsafe-inline` palavra-chave dentro do `script-src` diretiva para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts devido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Para corrigir esse problema, você deve</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) os scripts bloqueados usando o `SecureHtmlRenderer` classe.
1. Use o `CSPNonceProvider` para permitir que scripts sejam executados.
O Adobe Commerce e o Magento Open Source 2.4.7 e versões posteriores incluem uma **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar a geração de dados únicos [!DNL nonce] strings para cada solicitação. Esses [!DNL nonce] as cadeias de caracteres são anexadas ao [!UICONTROL CSP] cabeçalho.

   Use o `generateNonce` função em `Magento\Csp\Helper\CspNonceProvider` para obter uma [!DNL nonce] string.

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

1. [Adicionar um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao do seu módulo `csp_whitelist.xml` arquivo.

## Problema - O método de pagamento está ausente ou não está funcionando

Método de pagamento ausente ou inoperante no **checkout da loja** página, com o caractere &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
2. Adicione um produto ao carrinho e prossiga para a finalização.
3. Selecione um método de pagamento.

<u>Resultados esperados</u>:

Você pode selecionar um método de pagamento e prosseguir para colocar um pedido com sucesso.

<u>Resultados reais</u>:

O método de pagamento está ausente ou não está funcionando. As seguintes [!DNL JS] o erro é exibido no log do console do navegador: &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, **[!UICONTROL CSP]** está configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração e no `report-only` para todas as outras páginas.
Os correspondentes **[!UICONTROL CSP]** o cabeçalho não contém a variável `unsafe-inline` palavra-chave dentro do `script-src` diretiva para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts devido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Para corrigir esse problema, você deve</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) os scripts bloqueados usando o `SecureHtmlRenderer` classe.
1. Use o `CSPNonceProvider` para permitir que scripts sejam executados.
O Adobe Commerce e o Magento Open Source 2.4.7 e versões posteriores incluem uma **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar a geração de dados únicos [!DNL nonce] strings para cada solicitação. Esses [!DNL nonce] as cadeias de caracteres são anexadas ao [!UICONTROL CSP] cabeçalho.

   Use o `generateNonce` função em `Magento\Csp\Helper\CspNonceProvider` para obter uma [!DNL nonce] string.

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

1. [Adicionar um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao do seu módulo `csp_whitelist.xml` arquivo.

## Problema - o cliente não pode fazer um pedido

Um cliente não pode fazer um pedido com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
2. Adicione um produto ao carrinho e prossiga para a finalização.
3. Selecione um método de pagamento.
4. Clique em **Fazer pedido**.

<u>Resultados esperados</u>:

Você pode fazer um pedido com sucesso.

<u>Resultados reais</u>:

Você não pode fazer um pedido. As seguintes [!DNL JS] o erro é exibido no log do console do navegador: &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, **[!UICONTROL CSP]** está configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração e no `report-only` para todas as outras páginas.
Os correspondentes **[!UICONTROL CSP]** o cabeçalho não contém a variável `unsafe-inline` palavra-chave dentro do `script-src` diretiva para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts devido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Para corrigir esse problema, você deve</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) os scripts bloqueados usando o `SecureHtmlRenderer` classe.
1. Use o `CSPNonceProvider` para permitir que scripts sejam executados.
O Adobe Commerce e o Magento Open Source 2.4.7 e versões posteriores incluem uma **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] para facilitar a geração de dados únicos [!DNL nonce] strings para cada solicitação. Esses [!DNL nonce] as cadeias de caracteres são anexadas ao [!UICONTROL CSP] cabeçalho.

   Use o `generateNonce` função em `Magento\Csp\Helper\CspNonceProvider` para obter uma [!DNL nonce] string.

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

1. [Adicionar um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao do seu módulo `csp_whitelist.xml` arquivo.
