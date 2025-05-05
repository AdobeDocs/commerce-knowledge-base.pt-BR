---
title: 'ACSD-58141: PHPSESSID é gerado novamente nas solicitações do POST para clientes conectados com cache L2 Redis ativado'
description: Aplique o patch ACSD-58141 para corrigir o problema do Adobe Commerce em que "PHPSESSID" é regenerado em solicitações POST na área da Loja para um cliente conectado com cache L2 Redis ativado e o cliente é atualizado pelo administrador.
feature: Customers, Cache
role: Admin, Developer
exl-id: 72ae2ed4-bbac-472b-b257-3234f86000f4
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-58141: PHPSESSID é gerado novamente em [!DNL POST] solicitações para clientes conectados se o cache L2 Redis estiver habilitado

O patch ACSD-58141 corrige o problema em que `PHPSESSID` é regenerado em [!DNL POST] solicitações para um cliente conectado se o cache L2 Redis estiver habilitado e o cliente for atualizado do Administrador. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-58141. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce e do Magento Open Source:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`PHPSESSID` regenera em [!DNL POST] solicitações para um cliente conectado com o cache L2 Redis habilitado.

<u>Pré-requisitos</u>

O ambiente deve ser configurado com Redis com pelo menos 3 nós.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Crie um cliente e faça logon na Loja.
1. Verifique o valor de `PHPSESSID`.
1. Envie algumas solicitações [!DNL POST] (por exemplo, adicionar produto ao carrinho) e veja se `PHPSESSID` permanece o mesmo).
1. Faça logon no painel **[!UICONTROL Admin]** e altere o nome do meio do cliente.
1. Quando o nome do meio for salvo, altere-o e salve-o novamente algumas vezes.
1. Na loja, envie uma solicitação [!DNL POST]. `PHPSESSID` deveria ter sido atualizado.
1. Na loja, envie outra solicitação de [!DNL POST] e verifique `PHPSESSID`.
1. Repita a etapa anterior algumas vezes.

<u>Resultados esperados</u>

`PHPSESSID` é gerado novamente apenas uma vez depois de alterar os dados do cliente.

<u>Resultados reais</u>:

`PHPSESSID` é gerado novamente toda vez que as [!DNL POST] solicitações são enviadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
