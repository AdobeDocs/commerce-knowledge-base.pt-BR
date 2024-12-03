---
title: 'ACSD-53643: o pedido tem um total incorreto ao colocar um pedido de compra'
description: Aplique o patch ACSD-53643 para corrigir o problema do Adobe Commerce em que o pedido tem um total incorreto ao fazer um pedido com produtos desativados ou indisponíveis.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: o pedido tem um total incorreto ao colocar um pedido de compra

O patch ACSD-53643 corrige o problema em que o pedido tem um total incorreto ao fazer um pedido de compra com produtos desativados ou indisponíveis. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 está instalado. A ID do patch é ACSD-53643. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O total do pedido está incorreto ao fazer um pedido com produtos desativados ou indisponíveis.

<u>Etapas a serem reproduzidas</u>:

1. Instalar *[!UICONTROL B2B]* e *[!UICONTROL Inventory]*.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** e defina **[!UICONTROL Company]** = *Sim* e **[!UICONTROL Purchase Order]** = *Sim*.
1. Limpar cache de configuração.
1. Crie uma nova empresa, ative-a e habilite *[!UICONTROL Purchase order]* para a empresa.
1. Crie um novo usuário para a empresa.
1. Crie uma *Regra de aprovação* para aprovar todas as ordens com mais de *1 USD* pelo administrador da empresa.
1. Crie uma origem adicional.
1. Efetue logon como o novo usuário da empresa.
1. Adicione dois produtos ao carrinho e faça um pedido de compra.
1. Desative o segundo produto.
1. Faça logon como o administrador da empresa.
1. Abra a ordem de compra e veja se a ordem de compra contém ambos os produtos e o total é para ambos os produtos.
1. Aprovar a ordem de compra.
1. Coloque o pedido.
1. Abra os detalhes do pedido.

<u>Resultados esperados</u>:

* Não é possível fazer o pedido mesmo que um produto esteja *desativado* ou *esgotado*.
* O botão *[!UICONTROL Place Order]* está oculto.

<u>Resultados reais</u>:

O pedido feito contém apenas o primeiro produto ativo, mas o total do pedido é calculado para ambos os produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
