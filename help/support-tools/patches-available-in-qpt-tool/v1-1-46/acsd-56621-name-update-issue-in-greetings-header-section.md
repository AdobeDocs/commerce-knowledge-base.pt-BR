---
title: 'ACSD-56621: nomes atualizados não exibidos no cabeçalho de saudações para o usuário administrador da empresa'
description: Aplique o patch ACSD-56621 para corrigir o problema do Adobe Commerce em que o nome e o sobrenome atualizados do usuário administrador de empresa não são refletidos na seção do cabeçalho de saudações.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: nomes atualizados não exibidos no cabeçalho de saudações para o usuário administrador da empresa

O patch ACSD-56621 corrige o problema em que o nome e o sobrenome atualizados do usuário administrador de empresa não são refletidos na seção de cabeçalho de saudações. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. A ID do patch é ACSD-56621. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os nomes atualizados não são exibidos no cabeçalho de saudações para usuários administradores de empresas.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até o painel **[!UICONTROL Admin]**.
1. Vá para **[!UICONTROL Stores]** e selecione **[!UICONTROL Configuration]**.
1. Na seção **[!UICONTROL General]**, selecione **[!UICONTROL B2B]** para habilitar a funcionalidade de empresa B2B.
1. Vá para **[!UICONTROL Storefront]** e registre uma nova empresa.
1. Faça logon como o usuário administrador da empresa.
1. Vá para **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** e modifique os campos de nome e sobrenome conforme necessário.

<u>Resultados esperados</u>:

O nome e o sobrenome do usuário na seção de cabeçalho greetings são alterados imediatamente.

<u>Resultados reais</u>:

O nome e o sobrenome do usuário só são alterados quando o usuário faz logoff e logon novamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
