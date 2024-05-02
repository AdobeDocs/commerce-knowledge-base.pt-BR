---
title: "MDVA-30963: o filtro de pesquisa de produto administrativo não está funcionando como esperado"
description: O patch MDVA-30963 resolve o problema em que o Administrador do Commerce e o filtro de pesquisa de produto não funcionam como esperado. Os valores que são substituídos em um escopo de exibição de armazenamento também são considerados ao filtrar em **Todo o escopo de exibição de armazenamento**. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: o filtro de pesquisa de produto administrativo não está funcionando como esperado

O patch MDVA-30963 resolve o problema em que o Administrador do Commerce e o filtro de pesquisa de produto não funcionam como esperado. Os valores substituídos em um escopo de exibição de armazenamento também são considerados ao filtrar em **Exibição de todas as lojas** escopo de exibição de armazenamento. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.8 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Definir **Lojas** > **Configuração** > **Catálogo** > **Catálogo** > **Preço** > **Escopo do Preço de Catálogo** = *Site*.
1. Crie dois sites com duas moedas diferentes (por exemplo, o site padrão é uma loja na Índia \[Rúpia Rúpia\], e o segundo é a loja nos EUA \[Dólar $\]).
1. Defina o seguinte **Moeda de base**, **Moeda de Exibição Padrão**, e **Moedas permitidas**:
   * **Configuração padrão** = *Dólar Americano (Padrão)*
   * **Site principal** = *Rúpia indiana*
   * **WebsiteUS** = **Usar padrão** = *Dólar americano*
1. Definir **Lojas** > **Taxas de câmbio** = *1:1*.
1. Crie um produto de teste simples atribuído a ambos os sites com os seguintes preços:
   * **Preço padrão** = **Preço no site dos EUA** = *US$ 123*
   * **Preço do site principal** = *321 Rúpia*
1. Crie um usuário subAdmin que tenha acesso somente à Loja dos EUA.
1. Vá para a loja dos EUA e coloque um produto no carrinho (Exemplo: *Preço de US$ 123*).
1. Faça logon no Admin com o subAdmin recém-criado (Exemplo: *Somente administrador dos EUA*).
1. Ir para **Relatórios** > **Produtos no carrinho**.

<u>Resultados esperados</u>:

Ao filtrar no **Exibição de todas as lojas** escopo de exibição de loja, a filtragem de produtos deve obter o valor definido nesse escopo específico.

<u>Resultados reais</u>:

Os valores substituídos em um escopo de exibição de armazenamento também são considerados ao filtrar no escopo de exibição de armazenamento &quot;Todas as exibições de armazenamento&quot;.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
