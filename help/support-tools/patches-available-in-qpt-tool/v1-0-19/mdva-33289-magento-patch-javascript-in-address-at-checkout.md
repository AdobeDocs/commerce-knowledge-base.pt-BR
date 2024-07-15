---
title: "Patch MDVA-33289: Javascript no endereço na finalização"
description: O patch MDVA-33289 corrige o problema em que o Javascript mostra o endereço no pagamento. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-33289. Observe que o problema foi agendado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 247e4f05-7e89-4d37-b3d4-c2cae7595267
feature: Checkout, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Correção MDVA-33289: Javascript no endereço na finalização

O patch MDVA-33289 corrige o problema em que o Javascript mostra o endereço no pagamento. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-33289. Observe que o problema foi agendado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.4.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao fazer check-out com o Google Tag Manager (GTM) ativado, o Javascript é exibido no campo de endereço.

<u>Etapas a serem reproduzidas</u>:

1. Ativar GTM. Consulte o [Google Tag Manager](https://docs.magento.com/user-guide/marketing/google-tag-manager.html) em nosso guia do usuário, para obter detalhes.
1. Na loja, adicione alguns produtos ao carrinho.
1. Veja só.

<u>Resultado real</u>:

A seção de endereço é atualizada, mas inclui muito texto de código Javascript.

<u>Resultado esperado</u>:

O endereço é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
