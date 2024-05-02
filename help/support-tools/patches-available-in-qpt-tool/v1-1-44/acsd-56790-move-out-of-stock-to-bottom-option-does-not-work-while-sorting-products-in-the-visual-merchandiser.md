---
title: '"ACSD-56790: **[!UICONTROL move out of stock to bottom]** não funciona ao classificar produtos na variável  [!DNL Visual Merchandiser]'''
description: Aplique o patch ACSD-56790 para corrigir o problema do Adobe Commerce em que a opção de mover do estoque para o final não funciona ao classificar produtos no Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** não funciona ao classificar produtos na variável [!DNL Visual Merchandiser]

O patch ACSD-56790 corrige o problema em que a opção de mover do estoque para o final não funciona ao classificar produtos no [!DNL Visual Merchandiser]. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.44 está instalado. A ID do patch é ACSD-56790. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável **[!UICONTROL move out of stock to bottom]** não funciona ao classificar produtos na variável [!DNL Visual Merchandiser]

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crie os atributos a seguir.
1. Criar um novo site: **Não principal**.
1. Criar um **Loja não principal** neste novo site.
1. Criar dois armazenamentos:

   * Primeiro no **Loja do site principal**.
   * Segundo no **Loja não principal**.

1. Criar duas fontes:
   * Cartas.
   * Números.

1. Criar dois estoques:
   * Primeiro Principal - canais de vendas: Site Principal - fontes atribuídas: Cartas.
   * Segundo não principal - canais de vendas: Não principal - fontes atribuídas: Números.

1. Crie três produtos simples em ambos os sites, todos na categoria Padrão, todos atribuídos a ambas as fontes:

   * ProdutoA - Qtd. *10* em Cartas, Qtd. *0* em Números.
   * Produto1 - Qtd *0* em Cartas, Qtd. *10* em Números.
   * ProdutoA1 - Qtd. *10* em Cartas, Qtd. *10* em Números.

1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e selecione  **[!UICONTROL Default category]**.
1. Alterar o escopo para **Primeiro**.
1. Expanda os Produtos na seção Categoria.
1. Escolha a ordem de classificação como: **[!UICONTROL move out of stock to bottom]**

<u>Resultados esperados</u>:

A lista de produtos com o **esgotado** Os produtos da são movidos para a parte inferior.

<u>Resultados reais</u>:

Falha ao carregar os produtos. Uma página redireciona para o painel de administração com a mensagem de erro: `Invalid security or form key. Please refresh the page`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
