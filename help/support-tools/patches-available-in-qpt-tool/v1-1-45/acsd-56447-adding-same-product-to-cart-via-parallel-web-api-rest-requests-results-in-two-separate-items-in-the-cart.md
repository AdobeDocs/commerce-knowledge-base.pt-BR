---
title: 'ACSD-56447: Adicionar o mesmo produto ao carrinho por meio da API REST da Web paralela resulta em dois itens separados no carrinho'
description: Aplique o patch ACSD-56447 para corrigir o problema do Adobe Commerce em que adicionar o mesmo produto ao carrinho por meio de solicitações paralelas de API REST da Web resulta em dois itens separados no carrinho.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: Adicionar o mesmo produto ao carrinho por meio da API REST da Web paralela resulta em dois itens separados no carrinho

O patch ACSD-56447 corrige o problema em que adicionar o mesmo produto ao carrinho por meio de solicitações paralelas de API REST da Web resulta em dois itens separados no carrinho. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. A ID do patch é ACSD-56447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Adicionar o mesmo produto ao carrinho por meio de solicitações paralelas de API REST da Web resulta em dois itens separados no carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Gere um token de cliente para fazer a solicitação de chamadas de API REST usando [!DNL Postman].
1. Crie um carrinho de compras para o cliente.
1. Use o token gerado acima para criar um carrinho vazio para o cliente.
1. Use o CURL para fazer duas solicitações `AddProductsToCart` executadas em paralelo. Siga as instruções no [Tutorial de processamento de pedidos](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) na documentação do desenvolvedor.

<u>Resultados esperados</u>:

Itens com várias quantidades são mostrados em uma linha.

<u>Resultados reais</u>:

Os mesmos SKUs são mostrados em vários itens de linha.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
