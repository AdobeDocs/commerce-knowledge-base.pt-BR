---
title: O Adobe Commerce 2.3.6, 2.4.1 CAPTCHA no check-out não está funcionando
description: Este artigo fornece uma correção para o problema em que o recurso CAPTCHA para check-out não funciona como esperado na página Fazer pedido ao usar provedores de pagamento de terceiros, como Paypal Express, Payflow Pro ou CyberSource no Adobe Commerce.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# O Adobe Commerce 2.3.6, 2.4.1 CAPTCHA no check-out não está funcionando

Este artigo fornece uma correção para o problema em que o recurso CAPTCHA para check-out não funciona como esperado na página Fazer pedido ao usar provedores de pagamento de terceiros, como Paypal Express, Payflow Pro ou CyberSource no Adobe Commerce.

Este problema conhecido é mencionado em nossa documentação do desenvolvedor:

<u>Para Adobe Commerce 2.3.6</u>:

* [Notas de versão do Adobe Commerce 2.3.6: Problemas conhecidos](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/commerce-2-3-6.html)
* [Notas de versão do Magento Open Source 2.3.6: Problemas conhecidos](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Para Adobe Commerce 2.4.1</u>:

* [Notas de versão do Adobe Commerce 2.4.1: Problemas conhecidos](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-1#known-issues)
* [Notas de versão do Magento Open Source 2.4.1: Problemas conhecidos](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-1#known-issues)

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.3.6 e 2.4.1
* Magento Open Source 2.3.6 e 2.4.1

## Problema

<u>Etapas a serem reproduzidas</u>

1. Configure pelo menos um desses métodos de pagamento no Commerce: Paypal Express, Payflow Pro ou CyberSource.
1. Vá para **Admin > Lojas > Configuração > Clientes > Configuração do cliente > CAPTCHA** .
   * Defina **Habilitar CAPTCHA na Loja** = *Sim*.
   * Selecione no **Forms**: *Pedido de Check-out/Colocação*, *Logon* e *Esqueceu a senha*.
   * Definir **Modo de Exibição** = *Após o número de tentativas de logon* (para exibir a configuração **Número de Tentativas Sem Êxito de Logon**).
   * Defina **Number of Unsuccessful Attempts to Login** = *0* (para fazer o captcha funcionar o tempo todo).
1. No front-end, adicione um produto ao carrinho e tente fazer check-out.
1. Na página de informações de pagamento, insira captcha e tente finalizar a compra com Paypal Express, Payflow Pro ou CyberSource.

<u>Resultado esperado:</u>

O recurso CAPTCHA funciona conforme esperado.

<u>Resultado real:</u>

A mensagem de erro é exibida: *Forneça o código CAPTCHA e tente novamente.*

## Solução

Aplique um dos patches abaixo, dependendo se você está no Adobe Commerce no local/Adobe Commerce na infraestrutura de nuvem/Magento Open Source 2.3.6 ou 2.4.1.

## Correções

Os patches estão anexados a este artigo, disponíveis para download nos formatos `.composer` e `.git`.

Para baixar um patch, role até o final do artigo e clique no nome do arquivo ou clique em um dos links a seguir:

<u>Para Adobe Commerce no local/Adobe Commerce na infraestrutura de nuvem/Magento Open Source 2.3.6</u> :

* [Patch do compositor MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Patch do Git MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>Para Adobe Commerce no local/Adobe Commerce na infraestrutura de nuvem/Magento Open Source 2.4.1</u> :

* [Patch do compositor MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Patch do Git MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Esses patches não são compatíveis com nenhuma outra versão ou edição do Adobe Commerce ou Magento Open Source.

## Como aplicar o patch

<u>Correção do compositor</u>

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de suporte para obter instruções de patch de compositor.

<u>Patch do Git</u>

Consulte a documentação do desenvolvedor [Aplicação de patches: patches personalizados](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) para obter instruções de patch do Git para Adobe Commerce/Magento Open Source.
