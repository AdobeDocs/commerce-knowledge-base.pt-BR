---
title: 'MDVA-39923: A pesquisa por SKU na funcionalidade de ordem rápida B2B diferencia maiúsculas de minúsculas'
description: O patch MDVA-39923 corrige o problema em que os clientes recebem um erro ao pesquisar o pedido por SKU na funcionalidade de pedido rápido B2B com um caso diferente daquele com o qual o nome é salvo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-39923. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: A pesquisa por SKU na funcionalidade de ordem rápida B2B diferencia maiúsculas de minúsculas

O patch MDVA-39923 corrige o problema em que os clientes recebem um erro ao pesquisar o pedido por SKU na funcionalidade de pedido rápido B2B com um caso diferente daquele com o qual o nome é salvo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-39923. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A pesquisa por SKU na funcionalidade de ordem rápida B2B diferencia maiúsculas de minúsculas e mostra um erro quando uma caixa diferente é usada daquela com a qual o SKU é salvo.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador e acesse **Lojas** > **Configuração** > **B2B**.
1. Habilitar **Catálogo Compartilhado** e **Pedido Rápido**.
1. Crie um produto com SKU em maiúsculas, por exemplo, TEST20-1234
1. Atribuir o produto criado ao **Catálogo Compartilhado**.
1. Faça logon como cliente e clique em **Pedido rápido**.
1. Insira o SKU em minúsculas, por exemplo, test20-1234.

<u>Resultados esperados</u>:

O produto deve ser encontrado independentemente da caixa usada.

<u>Resultados reais</u>:

Mensagem de erro recebida: *1 produto(s) requer(em) sua atenção*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
