---
title: "ACSD-54472: os clientes de uma empresa rejeitada ainda podem autenticar"
description: Aplique o patch ACSD-54472 para corrigir o problema do Adobe Commerce em que os clientes de uma empresa rejeitada ainda podem se autenticar e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: os clientes de uma empresa rejeitada ainda podem autenticar

O patch ACSD-54472 corrige o problema em que os clientes de uma empresa rejeitada ainda podem se autenticar e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.40 está instalado. A ID do patch é ACSD-54472. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes de uma empresa rejeitada ainda podem se autenticar e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma empresa.
1. Adicionar produtos ao carrinho por meio de [!DNL GraphQL].
1. Alterar o status da empresa para *Bloqueado*.
1. Enviar um [!DNL GraphQL] solicitação para colocar a ordem e criar uma cotação negociável.
1. Alterar o status da empresa para *Rejeitado*.
1. Enviar um [!DNL GraphQL] solicitação para obter o token de autorização do usuário da empresa.
1. Definir status do cliente como *Inativo*.
1. Enviar um [!DNL GraphQL] solicitação para obter o token de autorização do usuário da empresa.

<u>Resultados esperados</u>:

* A ordem e a cotação negociável não são colocadas pelo usuário do *Bloqueado* empresa.
* O token de autorização não é obtido para o usuário do *Rejeitado* empresa.
* O token de autorização não é obtido para o *Inativo* cliente.

<u>Resultados reais</u>:

* A ordem e a cotação negociável são colocadas pelo usuário do *Bloqueado* empresa.
* O token de autorização é obtido para o usuário do *Rejeitado* empresa.
* O token de autorização é obtido para o *Inativo* cliente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
