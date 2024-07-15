---
title: "MDVA-30972: entrega incorreta de status de pedido criada por meio da API REST"
description: O patch MDVA-30972 resolve o problema em que o status do pedido é alterado incorretamente durante a criação do envio por meio da API REST. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: entrega incorreta de status de pedido criada via API REST

O patch MDVA-30972 resolve o problema em que o status do pedido é alterado incorretamente durante a criação do envio por meio da API REST. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 para 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando uma remessa parcial é criada pelo Administrador via API REST para um pedido com status de pedido *Suspeita de Fraude*, o status do pedido é alterado para *Processando*. Deve ficar em *Suspeita de fraude*.

<u>Pré-requisitos</u>:

* PayPal EC ou outro método de pagamento online está configurado.
* A integração para a API REST está configurada.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com dois ou mais itens.
1. Faça logon em **Administrador** > **Vendas** > **Pedidos**. Abra o pedido que acabou de criar.
1. Na página de detalhes do pedido, role até **Total de pedidos**. Clique no menu suspenso **Status** e selecione *Suspeita de fraude*. Em seguida, clique no botão **Enviar comentário**.
1. Verifique se o pedido tem o status *Suspeita de Fraude* agora.
1. Criar uma remessa para um item da ordem usando a API REST:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Abra o pedido no Administrador novamente e verifique seu status.

<u>Resultados esperados</u>:

* Status do Pedido = *Suspeita de Fraude*.
* O status do pedido não é alterado se a mesma entrega for criada a partir do Administrador.

<u>Resultados reais</u>:

Status do Pedido = *Processando*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
