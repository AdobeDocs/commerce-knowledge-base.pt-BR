---
title: 'ACSD-48164: o administrador restrito não pode salvar o valor no nível do site'
description: Aplique o patch ACSD-48164 para corrigir o problema do Adobe Commerce em que um administrador restrito não pode salvar um valor no nível do site.
exl-id: 6ec15163-ad30-4566-a46c-5756bfd9f8d4
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164: o administrador restrito não pode salvar o valor no nível do site

O patch ACSD-48164 corrige o problema em que um administrador restrito não pode salvar um valor no nível do site. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. A ID do patch é ACSD-48164. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O administrador restrito não pode salvar um valor no nível do site.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo site, loja e exibição de loja em [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Crie uma nova função de administrador em [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Vá para **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, selecione o novo site e atribua esta função a qualquer usuário administrador.

1. Selecione qualquer produto e atribua somente o novo site. Não selecione o site padrão.
1. Faça logon como o usuário administrador atribuído na etapa dois e edite o produto no escopo **[!UICONTROL All Store View]** alterando qualquer atributo de nível de site como *[!UICONTROL Status]*, *[!UICONTROL Tax Class]*, e defina o produto como novo.
1. Salve o produto.

<u>Resultados esperados</u>:

O usuário administrador associado ao escopo de função para um site pode salvar atributos de produto no nível do site usando o escopo *[!UICONTROL All Store View]*.

<u>Resultados reais</u>:

A mensagem de sucesso de que o produto foi salvo é exibida, mas os valores do atributo do produto permanecem inalterados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
