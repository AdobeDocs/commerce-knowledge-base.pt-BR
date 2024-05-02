---
title: "ACSD-56858: discrepância de permissões de função no administrador da empresa B2B"
description: Aplique o patch ACSD-56858 para corrigir o problema do Adobe Commerce em que as permissões de função são exibidas incorretamente para um administrador de empresa restrita no ambiente B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: discrepância de permissões de função no administrador da empresa B2B

O patch ACSD-56858 corrige o problema em que as permissões de função são exibidas incorretamente para um administrador de empresa restrita no ambiente B2B. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.47 está instalado. A ID do patch é ACSD-56858. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As permissões de função para um administrador de empresa restrito no ambiente B2B são exibidas incorretamente.

<u>Etapas a serem reproduzidas</u>:

1. Comece criando uma empresa, adicionando um administrador de empresa e usuários de empresa.
1. Faça logon como o administrador da empresa na loja e crie várias funções para usuários diferentes.
1. Atribua essas funções conforme necessário, como limitar o acesso a algumas tarefas enquanto permite o acesso total a outras.
1. Atribua essas funções com acesso total a um usuário diferente do administrador da empresa.
1. Faça logon em um usuário administrador que não seja da empresa, por exemplo, company_manager.
1. Navegue até **[!UICONTROL Roles and permission]** e edite a função.
1. Observe que as permissões exibidas não correspondem às permissões definidas no banco de dados da empresa para essa ID de função.

<u>Resultados esperados</u>:

As funções e permissões são exibidas corretamente para o usuário administrador não pertencente à empresa.

<u>Resultados reais</u>:

As funções não aparecem corretamente para o usuário administrador não-empresa conforme os registros do banco de dados na tabela de permissões.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
