---
title: "MDVA-35254: CAPTCHA de check-out funcionando incorretamente"
description: O patch MDVA-35254 corrige o problema com campos CAPTCHA não sendo exibidos após um número malsucedido de tentativas de finalização para pagamento de terceiros. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35254. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: CAPTCHA de check-out funcionando incorretamente

O patch MDVA-35254 corrige o problema com campos CAPTCHA não sendo exibidos após um número malsucedido de tentativas de finalização para pagamento de terceiros. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.19 está instalado. A ID do patch é MDVA-35254. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.1-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

Configurar CAPTCHA:

1. Instale e configure um provedor de pagamento de terceiros (Exemplo: Braintree).
1. Ir para **Loja > Configuração > Cliente > Configuração do cliente > CAPTCHA > Forms**.
1. Selecionar **Pedido de check-out/posicionamento**.
1. Mantenha a **Número de tentativas de login malsucedidas** como padrão (padrão = *3*).
1. Faça logon como cliente.
1. Adicione qualquer produto ao carrinho de compras.
1. Vá para a seção de pagamento no check-out.
1. Selecionar **Cartão de crédito** método de pagamento (Exemplo: Braintree).
1. Faça três tentativas de pagamento malsucedidas.

<u>Resultados esperados</u>:

O campo CAPTCHA é exibido quando o número de tentativas com falha é atingido.

<u>Resultados reais</u>:

O campo CAPTCHA nunca é exibido, somente a mensagem de erro: *Forneça o código CAPTCHA e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
