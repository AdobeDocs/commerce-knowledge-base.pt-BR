---
title: "Patch MDVA-31519: pedido perdido após check-out do convidado"
description: O patch MDVA-31519 resolve o problema em que os pedidos pagos estão ausentes e bloqueia os tempos limite de espera na finalização de compra do convidado.
exl-id: 2b4f9992-d58d-434f-adf8-d8ad8f761755
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Correção MDVA-31519: ordem perdida após a finalização da compra do convidado

O patch MDVA-31519 resolve o problema em que os pedidos pagos estão ausentes e bloqueia os tempos limite de espera na finalização de compra do convidado.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Habilitar check-out de convidado.
1. Crie uma regra de preço do carrinho sem um cupom (Exemplo: &quot;Frete gratuito acima de x valor&quot;).
1. Fazer uma grande quantidade de pedidos simultâneos de convidados envolvendo os PSPs (Payment Service Providers, provedores de serviços de pagamento) de API.

<u>Resultados esperados</u>:

Todas as transações de pagamento pagas são salvas no banco de dados e visíveis no Administrador, conforme esperado.

<u>Resultados reais</u>:

Somente uma pequena fração de pedidos é salva no banco de dados, enquanto a maioria das informações de pedidos é perdida devido a tempos limite de espera de bloqueio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
