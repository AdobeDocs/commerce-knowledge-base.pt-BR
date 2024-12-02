---
title: 'MDVA-37897: redirecionamento incorreto ao adicionar produtos de Visualizados recentemente'
description: O patch MDVA-37897 resolve o problema de redirecionamento incorreto quando os usuários tentam adicionar produtos com opções do widget Recentemente visualizado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalada. A ID do patch é MDVA-37897. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.4.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: redirecionamento incorreto ao adicionar produtos de Visualizados recentemente

O patch MDVA-37897 resolve o problema de redirecionamento incorreto quando os usuários tentam adicionar produtos com opções do widget Recentemente visualizado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalada. A ID do patch é MDVA-37897. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce em nossa infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando um usuário tenta adicionar um produto da seção Visualizado recentemente, que requer a seleção de opções, o usuário é redirecionado para a página da lista de produtos em vez da página de detalhes do produto.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com opções personalizáveis (Tipo: Botão de opção).
1. Configure o widget Visualizados recentemente para mostrar os produtos.
1. Visite produtos que têm opções personalizáveis para que eles sejam exibidos no widget Recentemente visualizados.
1. Clique em **Adicionar ao carrinho** em um dos produtos do widget Recentemente visualizado.

<u>Resultados esperados</u>:

Você será redirecionado para a página de detalhes do produto para escolher as opções.

<u>Resultados reais</u>:

Você será redirecionado para a página da lista de produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) em nossa documentação para desenvolvedores.
* Adobe Commerce em nossa infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) em nossa documentação de desenvolvedor.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
