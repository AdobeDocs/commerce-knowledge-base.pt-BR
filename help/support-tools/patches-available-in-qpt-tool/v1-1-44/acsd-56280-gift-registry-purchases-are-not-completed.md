---
title: "ACSD-56280: as compras do registro de presentes não estão concluídas"
description: Aplique o patch ACSD-56280 para corrigir o problema do Adobe Commerce em que as compras de registro de presentes não são concluídas
feature: Checkout
role: Admin
exl-id: 8e78ea1d-bd55-49d7-9d74-748b8f90e28c
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56280: As compras de registro de presentes não foram concluídas

O patch ACSD-56280 corrige o problema em que as compras de registro de presentes não são concluídas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. A ID do patch é ACSD-56280. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As compras do registro de presentes não foram concluídas.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como cliente e adicione um **[!UICONTROL product]** ao registro do presente.
1. Compartilhar o link do registro do presente.
1. Abra o link Registro de presente em outra janela do navegador/incógnita.
1. Adicione a quantidade e os itens ao carrinho.
1. Vá para o **[!UICONTROL Checkout Page]**, selecione **[!UICONTROL shipping method]**(Já que o endereço de envio já está selecionado, fornecido pelo inscrito).
1. Selecione o Método de pagamento.
1. Clique no botão Fazer pedido.

<u>Resultados esperados</u>:

O pedido deve ser feito.

<u>Resultados reais</u>:

A ordem não é feita e o erro exibido é, `Call to a member function getUpdatedQty() on null`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
