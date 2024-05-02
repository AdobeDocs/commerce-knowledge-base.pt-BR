---
title: "ACSD-45754: pontos de recompensa não adicionados após a aplicação de cupom ao carrinho"
description: O patch ACSD-45754 resolve o problema em que os pontos de recompensa não são adicionados após a aplicação de um cupom ao carrinho. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-45754. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: Pontos de premiação não adicionados após aplicar o cupom ao carrinho

O patch ACSD-45754 resolve o problema em que os pontos de recompensa não são adicionados após a aplicação de um cupom ao carrinho. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.18 está instalado. A ID do patch é ACSD-45754. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os pontos de premiação não são adicionados após a aplicação de um cupom ao carrinho.

<u>Pré-requisitos</u>:

O método de pagamento do PayPal está configurado.

<u>Etapas a serem reproduzidas</u>:

1. Criar taxas de câmbio de ponto de premiação acessando **Loja** > **Outras configurações** > **Taxas de câmbio de recompensa**.
1. Crie uma regra de preço do carrinho com um código de cupom para aplicar 100 pontos de recompensa aos clientes conectados.
1. Confira um produto como cliente conectado com o PayPal e o código do cupom.
1. Verifique o histórico de pontos de premiação na conta do cliente no administrador.

<u>Resultados esperados</u>:

Os pontos de recompensa são adicionados ao cliente de acordo com a regra de preço.

<u>Resultados reais</u>:

Nenhum ponto de premiação é adicionado ao cliente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
