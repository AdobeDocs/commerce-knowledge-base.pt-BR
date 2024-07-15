---
title: 'MDVA-43824: Falha na ação de cancelamento do pedido com o erro "Você não cancelou o item"'
description: 'O patch MDVA-43824 resolve o problema em que a ação de cancelamento do pedido falhou com o erro: *Você não cancelou o item*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43824. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.'
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824: Falha na ação de cancelamento do pedido com o erro &quot;Você não cancelou o item&quot;

O patch MDVA-43824 resolve o problema em que a ação de cancelamento do pedido falhou com o erro: *Você não cancelou o item*. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43824. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O pedido feito por um cliente conectado não pode ser cancelado. A ação de cancelamento do pedido falhou com o seguinte erro:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Etapas a serem reproduzidas</u>:

1. Crie uma regra de vendas (o tipo de cupom é &quot;Cupom específico&quot; ou &quot;Sem cupom&quot;).
1. Acesse a loja, faça logon como cliente e adicione um produto ao carrinho.
1. Vá para o carrinho e aplique a regra de preço do carrinho se a regra de preço do carrinho tiver um cupom como &quot;Cupom específico&quot;. A regra de preço do carrinho deve ser aplicada com sucesso.
1. Ir para checkout e fazer o pedido com qualquer forma de pagamento.
1. Acesse Administrador do Commerce > **Vendas** > **Pedidos**.
1. Abra o pedido feito na Etapa 4.
1. Clique no botão **Cancelar**.

<u>Resultados esperados</u>:

O pedido foi cancelado com êxito sem nenhum erro.

<u>Resultados reais</u>:

Falha na ação de cancelamento do pedido com o seguinte erro: *Você não cancelou o item.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
