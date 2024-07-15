---
title: "MDVA-30845: a finalização interrompe a conexão com o provedor de envio falha"
description: O patch MDVA-30845 corrige o problema em que o erro *Sorry, no quotes are available for this order at this time* é exibido ao falhar ao se conectar ao UPS XML/USPS/DHL durante o checkout e nenhum outro método de envio está disponível. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.2.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: falha na conexão do checkout com o provedor de envio

O patch MDVA-30845 corrige o problema em que o erro *Desculpe, nenhuma cotação está disponível para este pedido no momento* é exibido ao não se conectar ao UPS XML/USPS/DHL durante o check-out e nenhum outro método de envio está disponível. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.3.5-p2.

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura de nuvem 2.3.5-2.3.6.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Durante o check-out, o erro *Desculpe, não há cotações disponíveis para este pedido no momento* é exibido quando há uma falha na conexão com UPS XML/USPS/DHL e nenhum outro método de envio está disponível.

<u>Etapas a serem reproduzidas:</u>

1. Crie um produto.
1. Habilite e configure o método de envio UPS XML.
1. Adicionar o produto ao carrinho na loja.
1. Verifique se os métodos de envio UPS e frete de taxa fixa estão disponíveis.
1. Edite o arquivo de hosts para impedir que o USP se conecte ao gateway.
1. Na loja, tente obter as taxas e prosseguir para o check-out novamente.

<u>Resultado real:</u>

*Não há cotações disponíveis para este pedido no momento*. O erro é exibido e o frete de taxa fixa não está disponível.

<u>Resultado esperado:</u>

Nenhuma mensagem de erro exibida e o frete com taxa uniforme está disponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.


## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
