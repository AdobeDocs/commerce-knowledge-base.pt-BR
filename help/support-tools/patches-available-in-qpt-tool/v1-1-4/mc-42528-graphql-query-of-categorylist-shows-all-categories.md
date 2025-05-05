---
title: 'MC-42528: a consulta GraphQL de categoryList mostra todas as categorias'
description: O patch MC-42528 resolve o problema em que a consulta GraphQL de "categoryList" retorna categorias atribuídas e não atribuídas quando a Categoria de navegação de uma categoria específica é definida como "Deny". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 está instalada. A ID do patch é MC-42528. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: a consulta GraphQL de categoryList mostra todas as categorias

O patch MC-42528 resolve o problema em que a consulta GraphQL de `categoryList` retorna as categorias atribuídas e não atribuídas quando a Categoria de navegação de uma categoria específica é definida como &quot;Negar&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 está instalada. A ID do patch é MC-42528. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta GraphQL de `categoryList` retorna categorias atribuídas e não atribuídas.

<u>Etapas a serem reproduzidas</u>:

1. Crie duas categorias, CAT1 e CAT2, e atribua alguns produtos a cada categoria.
1. Criar um catálogo compartilhado privado.
1. Crie um usuário da empresa e atribua-o ao catálogo compartilhado criado.
1. Atribua CAT1 ao catálogo personalizado e defina a permissão de categoria como &quot;Permitir&quot; Categoria de Navegação para o grupo de clientes do catálogo privado.
1. Defina a permissão de categoria para CAT2 como &quot;Negar&quot; Categoria de navegação para o grupo de clientes do catálogo privado.
1. Execute a consulta do GraphQL `categoryList` ou `categories` como o usuário da empresa.

<u>Resultados esperados</u>:

Somente o CAT1 aparece na resposta.

<u>Resultados reais</u>:

Todas as categorias são exibidas na resposta, independentemente das permissões de navegação da categoria.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
