---
title: "ACSD-56616: Exibição de vitrine de produtos empacotados durante a escassez simples de estoque"
description: Aplique o patch ACSD-56616 para corrigir o problema do Adobe Commerce em que os produtos empacotados aparecem inesperadamente na loja quando todos os produtos simples associados estão esgotados.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: Exibição de vitrine de produtos empacotados durante a escassez simples de estoque.

O patch ACSD-56616 corrige o problema em que produtos empacotados aparecem inesperadamente na loja quando todos os produtos simples associados estão esgotados. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.45 está instalado. A ID do patch é ACSD-56616. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Exibição incorreta da loja de produtos empacotados durante falta simples de estoque.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo site/loja/loja.
1. Crie uma nova fonte.
1. Crie um novo estoque e atribua-o ao site recém-criado.
1. Configure os indexadores para atualizá-los de acordo com o cronograma.
1. Gere dois produtos simples, S1 (qtd. = 1) e S2 (qtd. = 1), e atribua-os ao novo estoque e ao novo site.
1. Criar *empacotado1* produto e associá-lo ao novo site, colocando-o na categoria *CAT*.
1. Definir duas opções suspensas necessárias e vincular um produto simples *S1* para option1 e *S2* para a opção 2.
1. Salve os produtos.
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** e habilitar *Adicionar código da loja ao URL* = *Sim*.
1. Abra a loja e compre o produto incluído.
1. Execute o cron duas vezes.
1. Retorne para a *CAT* categoria.

<u>Resultados esperados</u>:

A variável *pacote1* o produto está esgotado.

<u>Resultados reais</u>:

A variável *pacote1* o produto é visível com o preço = *$ 0*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
