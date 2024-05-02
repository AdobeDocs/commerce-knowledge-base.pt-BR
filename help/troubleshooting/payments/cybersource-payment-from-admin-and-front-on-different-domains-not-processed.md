---
title: Pagamento Cybersource de Admin e front em diferentes domínios não processado
description: Este artigo fornece uma correção para a limitação conhecida do Adobe Commerce 2.3.0 relacionada à não capacidade de processar pagamentos do Cybersource da loja e do administrador do Commerce, se estiverem em domínios diferentes.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Pagamento Cybersource de Admin e front em diferentes domínios não processado

Este artigo fornece uma correção para a limitação conhecida do Adobe Commerce 2.3.0 relacionada à não capacidade de processar pagamentos do Cybersource da loja e do administrador do Commerce, se estiverem em domínios diferentes.

>[!NOTE]
>
>A integração de pagamento principal do Adobe Commerce Cybersource está obsoleta desde a versão 2.3.3 e será completamente removida na versão 2.4.0. Use o [extensão oficial](https://marketplace.magento.com/cybersource-global-payment-management.html) do marketplace em vez disso.

## Problema

A implementação anterior da integração Cybersource permitiu o processamento de pagamentos apenas de um domínio. Como resultado, se sua loja Adobe Commerce estiver em um domínio diferente do administrador do Commerce, você receberá o seguinte erro ao tentar fazer um pedido usando o Cybersource no administrador: &quot; *Carga negada pelo X-Frame-Options: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ não permite enquadramento entre origens.* ..&quot;

<u>Etapas a serem reproduzidas</u>:

1. Configure o Admin em um subdomínio diferente.
1. Configurar o Cybersource para o armazenamento em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de pagamento** > **CyberSource**.
1. Ir para **Vendas** > **Pedidos**.
1. Criar novo pedido.
1. Criar novo cliente.
1. Informe os detalhes do cliente.
1. Informe os detalhes do pedido (produtos, método de entrega).
1. Selecione Cybersource como o método de pagamento.
1. Enviar pedido.

<u>Resultado esperado</u>: o pedido é feito sem problemas.

<u>Resultado real</u>: a página Pedido mostra um ícone de carregamento, mas o pedido nunca é feito. O erro é exibido no console.

## Solução

O patch anexado oferece a melhoria para a integração com o Cybersource. Depois de aplicar o patch, você precisa criar mais um perfil com o Cybersource para processar pagamentos no Administrador e adicionar as credenciais necessárias na configuração do Cybersource no Administrador do Commerce em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de pagamento** > **CyberSource**.

>[!NOTE]
>
>A melhoria está incluída no Adobe Commerce no local e na infraestrutura em nuvem 2.2.9 e 2.3.1.

## Correção

Há vários patches anexados a este artigo, diferentes patches para diferentes versões. Para baixar um patch, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

* [Baixar MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [Baixar MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [Baixar MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [Baixar MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Versões compatíveis do Adobe Commerce

Os patches foram criados para determinada versão anotada no nome do arquivo de patch. Por exemplo, MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch foi criado para o Adobe Commerce 2.1.9 e é o melhor patch a ser usado para essa versão.

Os patches também são compatíveis com as seguintes versões:

* Adobe Commerce no local 2.1.3-2.1.17; Adobe Commerce na infraestrutura em nuvem 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce no local 2.2.0 - 2.2.3; Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce no local 2.2.4-2.2.7; Adobe Commerce na infraestrutura em nuvem 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce no local 2.2.8, 2.3.0; Adobe Commerce na infraestrutura em nuvem 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Como aplicar um patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de conhecimento de suporte.

## Arquivos Anexados
