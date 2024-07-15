---
title: 'MDVA-30599: customer_is_guest está definido incorretamente'
description: O patch MDVA-30599 corrige o problema em que as cotações de convidado criadas usando a API são marcadas incorretamente como cotações para clientes conectados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. O problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_guest foi definido incorretamente

O patch MDVA-30599 corrige o problema em que as cotações de convidado criadas usando a API são marcadas incorretamente como cotações para clientes conectados. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. O problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.0

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As cotações de convidado criadas usando a API são marcadas incorretamente como cotações para clientes conectados.

<u>Etapas a serem reproduzidas</u>:

1. Na loja do Adobe Commerce, adicione um produto ao carrinho como usuário convidado.
1. No banco de dados do Adobe Commerce, localize o `quote_id_mask` correspondente.
1. Envie uma solicitação de API para a interface do Repositório de Carrinhos `quoteGuestCartRepositoryV1` para carrinhos convidados. Isso pode ser feito por meio de solicitação Swagger ou cURL.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Resultados esperados</u>:

Em resposta, você recebe `"customer_is_guest": true`

<u>Resultados reais</u>:

Em resposta, você recebe `"customer_is_guest": false`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Etapas adicionais necessárias após a instalação do patch

O patch será efetivo para todos os novos carrinhos de convidados. Se precisar corrigir carrinhos de convidados existentes, defina `quote.customer_is_guest = 1` para os registros em que `quote.customer_id` é NULL. Você pode executar uma consulta semelhante ao seguinte:

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Recomendamos testar a consulta no ambiente de preparo/integração antes de executá-la na produção. Também recomendamos ter um backup recente antes de qualquer manipulação com o DB.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
