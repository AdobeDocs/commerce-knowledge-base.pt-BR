---
title: Solução de problemas de criação de página de pedido no [!UICONTROL CSP] modo restrito
description: Este artigo explica os erros ao criar um pedido no lado do Administrador quando o modo restrito da CSP está Habilitado e fornece soluções para corrigir esses erros.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Solução de problemas de criação de página de pedido no [!UICONTROL CSP] modo restrito

Este artigo fornece explicações e correções para problemas do Adobe Commerce 2.4.7 ao criar um pedido no lado do administrador com **[!UICONTROL CSP restricted mode]** é *Ativado*, com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, Adobe Commerce no local e Magento Open Source:

* 2.4.7
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - Administrador **criar pedido** a página está quebrada ou não consegue carregar

O administrador **criar pedido** A página está quebrada ou não consegue carregar, com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Criar um novo pedido.

<u>Resultados esperados</u>:

O administrador **criar pedido** A página é carregada normalmente.

<u>Resultados reais</u>:

O administrador **criar pedido** A página está em branco ou tem componentes ausentes. As seguintes [!DNL JS] o erro é exibido no log do console do navegador: &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, **[!UICONTROL CSP]** está configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração e no `report-only` para todas as outras páginas.
Os correspondentes **[!UICONTROL CSP]** o cabeçalho não contém a variável `unsafe-inline` palavra-chave dentro do `script-src` diretiva para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts devido a [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

O método de pagamento está ausente ou não está funcionando no Administrador **página de criação do pedido**, com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Criar um novo pedido.
1. Crie um novo cliente.
1. Informe os detalhes do cliente.
1. Informe os detalhes do pedido (produtos, método de entrega).
1. Selecione um método de pagamento.

<u>Resultados esperados</u>:

Você pode selecionar um método de pagamento e prosseguir para colocar um pedido com sucesso.

<u>Resultados reais</u>:

O método de pagamento está ausente ou não está funcionando. As seguintes [!DNL JS] o erro é exibido no log do console do navegador: &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;.

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, **[!UICONTROL CSP]** está configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração e no `report-only` para todas as outras páginas.
Os correspondentes **[!UICONTROL CSP]** o cabeçalho não contém a variável `unsafe-inline` palavra-chave dentro do `script-src` diretiva para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts devido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

1. [adicionar um [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) ao do seu módulo `csp_whitelist.xml` arquivo.

## Problema - O administrador não pode fazer um pedido

Um administrador não pode enviar um pedido para o Administrador **criar página de pedido**, com o &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;mensagem de erro no log do console do navegador.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Criar um novo pedido.
1. Crie um novo cliente.
1. Informe os detalhes do cliente.
1. Informe os detalhes do pedido (produtos, método de entrega).
1. Selecione um método de pagamento.
1. Enviar o pedido.

<u>Resultados esperados</u>:

Você pode enviar um pedido com sucesso.

<u>Resultados reais</u>:

Você não pode enviar um pedido. As seguintes [!DNL JS] o erro é exibido no log do console do navegador: &quot;*Recusou-se a executar o script integrado porque ele viola a seguinte diretiva de política de segurança de conteúdo: &quot;script-src ...*&quot;

### Causa

No Adobe Commerce e Magento Open Source versões 2.4.7 e posteriores, **[!UICONTROL CSP]** está configurado em `restrict-mode`, por padrão, para páginas de pagamento nas áreas de vitrine e administração e no `report-only` para todas as outras páginas.
Os correspondentes **[!UICONTROL CSP]** o cabeçalho não contém a variável `unsafe-inline` palavra-chave dentro do `script-src` diretiva para páginas de pagamento. Além disso, somente [!DNL whitelisted] scripts integrados são permitidos.

### Solução

Os usuários podem ver erros de navegador devido ao bloqueio de determinados scripts devido a **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
