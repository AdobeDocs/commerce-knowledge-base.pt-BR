---
title: "ACSD-52398: A quantidade solicitada não está disponível ao tentar atualizar a quantidade do produto agrupado"
description: Aplique o patch ACSD-52398 para corrigir o problema do Adobe Commerce em que a quantidade solicitada não está disponível ao tentar atualizar a quantidade de um produto empacotado no carrinho na loja.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: A quantidade solicitada não está disponível ao tentar atualizar a quantidade do produto agrupado

O patch ACSD-52398 corrige o problema em que a quantidade solicitada não está disponível ao tentar atualizar a quantidade de um produto empacotado no carrinho na loja. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52398. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade solicitada não está disponível ao tentar atualizar a quantidade de um produto agrupado no carrinho na loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos simples com a quantidade *1* e *10*.
1. Crie um produto empacotado usando os produtos simples.
1. Adicione o produto incluído ao carrinho.
1. Edite o produto e tente atualizar a quantidade para *3* para a opção em que *10* itens estão disponíveis.

<u>Resultados esperados</u>:

Não há erros. A quantidade foi atualizada com êxito, pois há *10* itens em estoque para esta opção.

<u>Resultados reais</u>:

O seguinte erro é lançado: *A quantidade solicitada não está disponível*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
