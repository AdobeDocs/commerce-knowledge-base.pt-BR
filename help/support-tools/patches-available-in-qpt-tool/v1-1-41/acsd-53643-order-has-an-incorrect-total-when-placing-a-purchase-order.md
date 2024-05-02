---
title: "ACSD-53643: o pedido tem um total incorreto ao colocar um pedido de compra"
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

O patch ACSD-53643 corrige o problema em que o pedido tem um total incorreto ao fazer um pedido de compra com produtos desativados ou indisponíveis. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.41 está instalado. A ID do patch é ACSD-53643. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O total do pedido está incorreto ao fazer um pedido com produtos desativados ou indisponíveis.

<u>Etapas a serem reproduzidas</u>:

1. Instalar *[!UICONTROL B2B]* e *[!UICONTROL Inventory]*.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** e defina **[!UICONTROL Company]** = *Sim* e **[!UICONTROL Purchase Order]** = *Sim*.
1. Limpar cache de configuração.
1. Criar uma nova empresa, ativá-la e habilitar *[!UICONTROL Purchase order]* para a empresa.
1. Crie um novo usuário para a empresa.
1. Criar um *Regra de aprovação* para aprovar todas as ordens de mais de *US$ 1* pelo administrador da empresa.
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

* Não é possível fazer o pedido mesmo que um produto no pedido esteja *desabilitado* ou *sem estoque*.
* *[!UICONTROL Place Order]* está oculto.

<u>Resultados reais</u>:

O pedido feito contém apenas o primeiro produto ativo, mas o total do pedido é calculado para ambos os produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
