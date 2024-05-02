---
title: "ACSD-47875: não é possível adicionar o produto ao carrinho para o escopo de exibição da loja com o gerenciamento de estoque"
description: Aplique o patch ACSD-47875 para corrigir o problema do Adobe Commerce em que um produto não pode ser adicionado ao carrinho do cliente do Administrador para um escopo de exibição de loja específico com gerenciamento de estoque.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: Não é possível adicionar o produto ao carrinho para o escopo de exibição da loja com o gerenciamento de estoque

O patch ACSD-47875 corrige o problema em que um produto não pode ser adicionado a um carrinho do cliente do Administrador para um escopo de exibição de loja específico com gerenciamento de estoque. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.36 está instalado. A ID do patch é ACSD-47875. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores não podem adicionar um produto ao carrinho do cliente usando o **[!UICONTROL Manage Shopping Cart]** recurso no Administrador para um escopo de exibição de loja específico com MSI instalado.

<u>Pré-requisitos</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] Os módulos do são instalados e ativados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site, uma loja e uma visualização de loja.
1. Criar uma fonte adicional diferente de *Padrão*.
1. Crie um novo estoque e atribua-o ao novo site e à nova fonte.
1. Crie um novo cliente para o novo site.
1. Atribuir um produto somente ao novo site; cancelar atribuição do site padrão.

   * Atribuir a nova origem e definir Qtd. *acima de 0* para a nova origem e *0* para a origem padrão.

1. Vá para a **[!UICONTROL Customer Edit]** na página Admin. Clique em **[!UICONTROL Manage Shopping Cart]**.
1. Altere o escopo de exibição de loja para a nova exibição de loja.
1. Vá para a **[!UICONTROL Products]** seção e pesquisar o produto.
1. Selecione o produto e clique **[!UICONTROL Add selections to my cart]**.

<u>Resultados esperados</u>:

O produto é adicionado ao carrinho.

<u>Resultados reais</u>:

* O seguinte erro é lançado: *O produto que você está tentando adicionar não está disponível.*
* O produto não é adicionado ao carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
