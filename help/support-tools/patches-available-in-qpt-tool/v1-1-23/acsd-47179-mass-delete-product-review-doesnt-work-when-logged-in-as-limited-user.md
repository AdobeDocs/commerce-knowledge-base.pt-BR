---
title: "ACSD-47179: a exclusão em massa de análises de produtos não funciona quando conectado como função de usuário limitada"
description: Aplique o patch ACSD-47179 para corrigir o problema do Adobe Commerce em que a exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada.
exl-id: 85d7ce63-7dd6-4df4-b314-278d18e69fbb
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-47179: a exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada

O patch ACSD-47179 corrige o problema em que a exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.23 está instalado. A ID do patch é ACSD-47179. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada.

<u>Etapas a serem reproduzidas</u>:

1. Criar um site secundário.
1. Crie uma função de usuário restrita ao site secundário com permissão total para as seguintes seções:
   * Catálogo
   * Cliente
   * Marketing
1. Crie um produto e atribua-o ao site secundário.
1. Adicione duas análises ao produto a partir do front-end.
1. Faça logon no [!DNL Commerce] Administrador usando o usuário administrador restrito recém-criado.
1. Tente excluir em massa as revisões pendentes.

<u>Resultados esperados</u>:

Um administrador com permissões suficientes pode excluir em massa as revisões pendentes.

<u>Resultados reais</u>:

Você recebe o seguinte erro: _Algo deu errado. Exceção gerada em support_report.log_

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
