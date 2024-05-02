---
title: "ACSD-46869: produtos configuráveis não são atualizados usando a API REST no check-out"
description: O patch ACSD-46869 corrige o problema em que os produtos configuráveis não são atualizados usando a API REST na finalização. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 está instalada. A ID do patch é ACSD-46869. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: produtos configuráveis não são atualizados usando a API REST no check-out

O patch ACSD-46869 corrige o problema em que os produtos configuráveis não são atualizados usando a API REST na finalização. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.20 está instalado. A ID do patch é ACSD-46869. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL QPT] landing page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos configuráveis não são atualizados usando a API REST durante o check-out.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com atributos de cor e tamanho.
1. Selecionar **[!UICONTROL Options]** e adicionar o produto ao carrinho.
1. Ir para **[!UICONTROL Checkout]**, atualize o tamanho várias vezes, exceto por qtd., e verifique a solicitação e a resposta.
1. Você recebe a seguinte resposta ao atualizar o tamanho.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Resultados esperados</u>:

O valor é atualizado de acordo com as alterações.

<u>Resultados reais</u>:

`option_value` não é atualizado, portanto, quando o pedido é feito, ele tem o valor do tamanho antigo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tools] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) na guia Ferramenta de correções de qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no [!DNL QPT], consulte [Patches disponíveis em [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na guia Ferramenta de correções de qualidade.
