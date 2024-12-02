---
title: 'MDVA-37725: Emails enviados por sites não padrão contêm URLs de logotipo do site padrão'
description: O patch MDVA-37725 corrige o problema em que emails de ordem assíncrona são enviados por sites não padrão contendo URLs de logotipo do site padrão.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: Emails enviados por sites não padrão contêm URLs de logotipo do site padrão

>[!WARNING]
>
> O patch MDVA-37725 está obsoleto.

O patch MDVA-37725 corrige o problema em que emails de ordem assíncrona são enviados por sites não padrão contendo URLs de logotipo do site padrão. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 está instalada. A ID do patch é MDVA-37725. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Emails de pedido assíncrono são enviados por sites não padrão contendo os URLs do logotipo do site padrão.

<u>Pré-requisitos</u>:

1. O segundo site/loja/exibição de loja deve ter sido criado.
1. A configuração de **Envio Assíncrono** deve ser habilitada em **Lojas** > **Configurações** > **Configuração** > **Vendas** > **Email de Vendas** > **Configurações Gerais**.
1. A configuração **Adicionar Código de Repositório às URLs** está ativada para facilitar o acesso ao site secundário de **Lojas** > **Configurações** > **Configuração** > **Opções de URL**.

<u>Etapas a serem reproduzidas</u>:

1. Fazer pedidos da primeira e da segunda loja.
1. Execute cron para enviar os emails de vendas.
1. Verifique o email do segundo site.

<u>Resultados esperados</u>:

O URL do logotipo do email contém o URL do segundo site.

<u>Resultados reais</u>:

O URL do logotipo do email contém o URL do site padrão.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
