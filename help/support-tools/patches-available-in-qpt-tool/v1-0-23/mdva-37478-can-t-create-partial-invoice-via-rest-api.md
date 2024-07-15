---
title: "MDVA-37478: Não é possível criar fatura parcial por meio da API REST"
description: O patch MDVA-37478 corrige o problema quando não é possível criar uma fatura parcial por meio da API REST para um pedido feito com a forma de pagamento **Pagamento na conta**. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalada. A ID do patch é MDVA-37478. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: Não é possível criar fatura parcial via API REST

O patch MDVA-37478 corrige o problema quando você não consegue criar uma fatura parcial via API REST para um pedido feito com o método de pagamento **Pagamento na conta**. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalada. A ID do patch é MDVA-37478. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.3-p1
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.0-2.3.7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisito</u>:

Adobe Commerce com módulo B2B instalado

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **empresa B2B**.
1. Habilitar o método de pagamento **Pagamento na Conta**.
1. Crie 2 produtos simples.
1. Crie uma conta de empresa.
1. Adicione créditos da empresa que excedem o preço total de 2 produtos criados.
1. Faça logon no front-end usando a conta da empresa criada.
1. Adicione os 2 produtos criados ao carrinho e finalize a compra usando o método de pagamento **Pagamento na conta**.
1. Tente criar uma fatura parcial para o pedido criado pela API REST:

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Resultados esperados</u>:

A fatura parcial é criada para um pedido feito usando o método de pagamento **Pagamento na Conta**, conforme esperado.

<u>Resultados reais</u>:

O seguinte erro é retornado da API REST:

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
