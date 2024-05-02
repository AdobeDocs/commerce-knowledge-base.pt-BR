---
title: "MDVA-29446: método de envio não relevante disponível para check-out"
description: O patch MDVA-29446 resolve o problema em que um método de envio que não é aplicável aparece nas opções do método de envio de finalização de compra e, se selecionado, uma mensagem de erro "*A operadora com esse método não é encontrada nula, com taxa uniforme*." é exibido. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. O problema está programado para ser corrigido em versões posteriores do Adobe Commerce.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: método de envio não relevante disponível para check-out

O patch MDVA-29446 resolve o problema em que um método de envio que não é aplicável aparece nas opções de método de envio de check-out e, se selecionado, uma mensagem de erro &quot;*A portadora com esse método não foi encontrada como nula, taxa uniforme*.&quot; é exibido. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.6 está instalado. O problema está programado para ser corrigido em versões posteriores do Adobe Commerce.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 - 2.4.0.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problemas

Você tem um método de envio que não é aplicável, mas ainda é exibido nas opções de método de envio de check-out e pode selecionar esse método de envio não relevante.

<u>Etapas a serem reproduzidas</u>:

1. Instale o clean 2.3-develop.
1. Habilitar Taxa única e definir:

   * País de Destino Aplicável = *Países específicos*
   * Países Específicos para Entrega = *Antártida*
   * Mostrar Método se Não Aplicável = *Sim*

1. Desative todos os outros métodos de envio.
1. Acesse o front-end e crie um cliente com um endereço dos EUA.
1. Selecione um item e clique em **Adicionar ao carrinho**.
1. Clique no carrinho e clique em **Prosseguir para o check-out**.

<u>Resultados reais</u>:

1. No **Envio** página, você verá o seguinte:

   * Taxa uniforme visível
   * Taxa única de US$ 0
1. Depois que o usuário clicar **Próxima**, o usuário recebe o seguinte erro:

*&quot;Portadora com esse método não encontrada: null, flatrate&quot;*

<u>Resultados esperados</u>:

* O preço do método de envio não é visível se o método de envio não for aplicável.
* A variável **Próxima** O botão não deve estar ativo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
