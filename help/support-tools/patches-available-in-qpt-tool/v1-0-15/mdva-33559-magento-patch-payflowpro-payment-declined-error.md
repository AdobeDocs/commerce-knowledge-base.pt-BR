---
title: "Correção MDVA-33559: erro recusado no pagamento do PayflowPro"
description: O patch MDVA-33559 resolve o problema em que os pagamentos do PayPal PayflowPro são recusados.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Correção MDVA-33559: erro recusado no pagamento do PayflowPro

O patch MDVA-33559 resolve o problema em que os pagamentos do PayPal PayflowPro são recusados.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.15 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A questão diz respeito aos caracteres especiais &quot;E&quot; comercial (&amp;) e &quot;sinal de igual (=)&quot; utilizados nos nomes.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um produto simples ao carrinho.
1. Vá para o check-out.
1. Defina o endereço de entrega. (Exemplo de endereço de entrega: **Nome** = ** *John&#39;s* **  **Sobrenome** = ** *Apple &amp; Oranges, Inc* **  **Endereço** = *1234 E Sem Nome St*  **País** = *EUA*  **Estado/Província** = *Qualquer estado*  **Cidade** = *Qualquer cidade*  **Zip** = *12345*  **Telefone** = *1234567890*)
1. Definir pagamento para **PayPal PayflowPro** e tente concluir o check-out.

<u>Resultados esperados</u>:

A transação resulta em um pagamento bem-sucedido ou em uma mensagem de erro correta, conforme esperado.

<u>Resultados reais</u>:

A transação é recusada e o cliente recebe um email dizendo: &quot;A transação foi recusada&quot;.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
