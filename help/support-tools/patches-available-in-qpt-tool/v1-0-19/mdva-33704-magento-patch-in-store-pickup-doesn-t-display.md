---
title: "Correção do MDVA-33704: a coleta na loja não é exibida"
description: O patch MDVA-33704 resolve o problema em que os produtos com a opção de coleta na loja não são exibidos como um método de envio.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Correção do MDVA-33704: a coleta na loja não é exibida

O patch MDVA-33704 resolve o problema em que os produtos com a opção de coleta na loja não são exibidos como um método de envio.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.19 está instalado. A ID do patch é MDVA-33704. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.4.0-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito</u>:<br>

**Escolher na loja** habilitado

<u>Etapas a serem reproduzidas</u>:

1. Adicione um produto ao carrinho.
1. Vá para Check-out.
1. Adicione informações de envio e escolha qualquer método de envio diferente da retirada na loja.
1. Selecionar **Continuar para pagamento**, mas não prossiga para a página de pagamento.
1. Em vez disso, volte para a **Contato e envio** seção.
1. Selecionar **Retirada**.
1. Selecionar **Loja** e **Clique para pagar**.
1. Observe que seu endereço de entrega é inserido automaticamente como um endereço de cobrança.
1. Atualize a página da Web.

<u>Resultados esperados</u>:

A opção de retirada na loja será exibida como um método de envio, conforme esperado.

<u>Resultados reais</u>:

A opção de retirada na loja não será exibida como um método de envio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
