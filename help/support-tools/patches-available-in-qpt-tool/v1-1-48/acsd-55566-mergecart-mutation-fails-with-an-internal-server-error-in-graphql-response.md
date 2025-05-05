---
title: 'ACSD-55566: falha na mutação [!UICONTROL mergeCart] com erro interno do servidor na resposta  [!DNL GraphQL] '
description: Aplique o patch ACSD-55566 para corrigir o problema do Adobe Commerce em que a mutação "mergeCart" falha com um erro interno do servidor na resposta  [!DNL GraphQL]  ao mesclar os carrinhos de origem e de destino que têm os mesmos itens de pacote.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566: falha na mutação `mergeCart` com erro interno do servidor na resposta [!DNL GraphQL]

O patch ACSD-55566 corrige o problema em que a mutação `mergeCart` falha com um erro interno do servidor na resposta [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. A ID do patch é ACSD-55566. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mutação `mergeCart` falha com um erro de servidor interno na resposta [!DNL GraphQL] ao mesclar os carrinhos de origem e destino que têm os mesmos itens de pacote.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma fonte personalizada e um estoque personalizado.
1. Atribua o estoque criado ao site principal.
1. Crie um produto simples e atribua a ele a origem criada (qtd.=2).
1. Crie um produto combinado com uma opção e um produto secundário (produto criado na etapa 3).
1. Crie um carrinho de convidados via [!DNL GraphQL].
1. Adicione um produto do pacote com ambas as opções selecionadas.
1. Salve a *cartID*.
1. Crie um cliente e gere um token de cliente.
1. Crie um carrinho do cliente.
1. Adicione o mesmo produto do pacote com a mesma configuração ao carrinho.
1. Tente mesclar o carrinho de convidado com o carrinho do cliente.

<u>Resultados esperados</u>:

O carrinho do cliente contém produtos de ambos os carrinhos.

<u>Resultados reais</u>:

Você recebe um erro interno.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
