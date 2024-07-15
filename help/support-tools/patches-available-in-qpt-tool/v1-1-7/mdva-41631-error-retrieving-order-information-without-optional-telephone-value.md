---
title: 'MDVA-41631: Erro ao recuperar informações do pedido sem valor "phone" opcional'
description: O patch MDVA-41631 corrige o problema em que os usuários obtêm um erro ao recuperar informações do pedido sem o valor opcional de "telefone" por meio do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: erro ao recuperar informações do pedido sem valor &quot;phone&quot; opcional

O patch MDVA-41631 corrige o problema em que os usuários obtêm um erro ao recuperar informações do pedido sem o valor opcional de &quot;telefone&quot; por meio do GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários recebem um erro ao recuperar informações do pedido sem o valor opcional de &quot;telefone&quot; por meio do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Loja** > **Configuração** > **Clientes** > **Configuração do Cliente** > **Opções de Nome e Endereço** > **Mostrar Telefone** e defina o número de telefone como opcional.
1. Faça um pedido usando a API do GraphQL como cliente conectado.
   * Não defina o número de telefone ao definir os endereços de faturamento e de envio. Siga as instruções fornecidas no [Tutorial de check-out do GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) em nossa documentação do desenvolvedor.
1. Recupere o pedido usando a [consulta customerOrders](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html) do GraphQL.

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Resultados esperados</u>:

Os usuários obtêm informações sobre pedidos.

<u>Resultados reais</u>:

Os usuários recebem o seguinte erro: *&quot;mensagem&quot;: &quot;Erro interno do servidor&quot;,*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
