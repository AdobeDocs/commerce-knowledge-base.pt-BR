---
title: "ACSD-42807: o sinal de moeda personalizado não é exibido na loja"
description: O patch ACSD-42807 corrige o problema em que o sinal de moeda personalizado não é exibido na loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-42807. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: o sinal de moeda personalizado não é exibido na vitrine

O patch ACSD-42807 corrige o problema em que o sinal de moeda personalizado não é exibido na loja. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.17 está instalado. A ID do patch é ACSD-42807. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O sinal de moeda personalizado não é exibido na loja.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Loja** > **Configurações** > **Configurações** > **Geral** > **Configuração de moeda** e selecione qualquer moeda personalizada. Por exemplo, **Peso mexicano**.
1. Ir para **Loja** > **Configurações** > **Configurações** > **Geral** > **Opções de localidade** e selecione **Espanhol (México)**.
1. Ir para **Loja** > **Símbolos de moeda** e configure o símbolo da moeda para **MX$**.
1. Verifique o símbolo da moeda no front-end.

<u>Resultados esperados</u>:

O símbolo de moeda padrão é &quot;MX$&quot; com a moeda definida como &quot;Peso mexicano&quot; e o local definido como &quot;Espanhol (México)&quot;.

<u>Resultados reais</u>:

O símbolo de moeda padrão mostra &quot;$&quot;.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
