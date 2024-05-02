---
title: "ACSD-48164: o administrador restrito não pode salvar o valor no nível do site"
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

O patch ACSD-48164 corrige o problema em que um administrador restrito não pode salvar um valor no nível do site. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.27 está instalado. A ID do patch é ACSD-48164. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O administrador restrito não pode salvar um valor no nível do site.

<u>Etapas a serem reproduzidas</u>:

1. Criar um novo modo de exibição de site, loja e loja no [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Criar uma nova função de administrador no [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Ir para **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, selecione o novo site e atribua essa função a qualquer usuário administrador.

1. Selecione qualquer produto e atribua somente o novo site. Não selecione o site padrão.
1. Faça logon como o usuário administrador atribuído na etapa dois e edite o produto em **[!UICONTROL All Store View]** ao alterar qualquer atributo no nível do site, como *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* e defina o produto como novo.
1. Salve o produto.

<u>Resultados esperados</u>:

O usuário administrador associado ao escopo da função em um site pode salvar atributos de produto no nível do site usando o *[!UICONTROL All Store View]* âmbito de aplicação.

<u>Resultados reais</u>:

A mensagem de sucesso de que o produto foi salvo é exibida, mas os valores do atributo do produto permanecem inalterados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
