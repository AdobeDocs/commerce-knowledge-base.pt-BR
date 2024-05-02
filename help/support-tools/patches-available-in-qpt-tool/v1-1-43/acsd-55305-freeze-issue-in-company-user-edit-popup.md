---
title: '"ACSD-55305: Congelamento de pop-ups durante a edição de usuários da empresa no [!UICONTROL My Account]'''
description: Aplique o patch ACSD-55305 para corrigir o problema do Adobe Commerce em que [!UICONTROL Edit Company User] pop-up na [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] A página congela com um carregador na tela.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: Congelamento de pop-ups durante a edição de usuários da empresa no [!UICONTROL My Account]

O patch ACSD-55305 corrige o problema em que  [!UICONTROL Edit Company User] pop-up na [!UICONTROL My Account]> [!UICONTROL Company Structure] A página congela com um carregador na tela. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.43 está instalado. A ID do patch é ACSD-55305. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro ao tentar usar o *[!UICONTROL Edit Company User]* pop-up na *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* página, conforme congela com um carregador exibido na tela.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma empresa B2B.
1. Crie um atributo de seleção múltipla para clientes.
1. Atribua um valor ao atributo recém-criado para o administrador da empresa.
1. Faça logon como Administrador da empresa.
1. Vá para a [!UICONTROL account dashboard] e navegue até o **[!UICONTROL Company Structure]**.
1. Selecione o usuário.
1. Clique em **[!UICONTROL Edit Selected]**.

<u>Resultados esperados</u>:

O pop-up do formulário é exibido com precisão, fornecendo a opção para editar as informações da empresa.

<u>Resultados reais</u>:

O pop-up do formulário é exibido sem qualquer possibilidade de edição.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
