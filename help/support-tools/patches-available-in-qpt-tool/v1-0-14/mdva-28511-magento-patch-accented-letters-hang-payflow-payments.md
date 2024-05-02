---
title: "MDVA-28511: cartas acentuadas suspendem pagamentos de Fluxo de Pagamento"
description: O patch MDVA-28511 resolve o problema quando os pagamentos por meio do **Payflow Pro** não são concluídos para nomes de clientes com letras acentuadas.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511: pagamentos de fluxo de pagamento de cartas acentuadas

O patch do MDVA-28511 resolve o problema quando os pagamentos por meio do **Fluxo de pagamento Pro** não preencha para nomes de clientes com letras acentuadas.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.14 está instalado. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito</u>:

Ativar **Fluxo de pagamento Pro** método de pagamento de cartão de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um produto ao carrinho e continue para a página de check-out.
1. Defina um nome de cliente com letras acentuadas. (Exemplo: **Étienne Ãillin**)
1. Prossiga para as etapas de pagamento.
1. Selecionar **Fluxo de pagamento Pro** as **Cartão de crédito** e preencha os detalhes do cartão de crédito.
1. Clique em **Fazer pedido** botão.

<u>Resultados esperados</u>:

O pedido é concluído sem nenhum problema, conforme esperado.

<u>Resultados reais</u>:

O pedido não é concluído e os registros mostrarão um erro semelhante ao deste exemplo:

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
