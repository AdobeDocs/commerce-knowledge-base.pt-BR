---
title: "MDVA-29042: permissões de categoria global inalteradas"
description: O patch MDVA-29042 corrige o problema em que as permissões do catálogo eram alteradas para "*Permitir*" automaticamente depois que um novo produto era adicionado ao catálogo compartilhado no Administrador do Commerce. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.6 com a extensão B2B.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: permissões de categoria global inalteradas

O patch MDVA-29042 corrige o problema em que as permissões do catálogo foram alteradas para &quot;*Permitir*&quot; automaticamente depois que um novo produto é adicionado ao catálogo compartilhado no Administrador do Commerce. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.5 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.3.6 com a extensão B2B.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.3.3 para 2.3.4-p2 com extensão B2B

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Desmarcar um grupo de clientes nas permissões de categoria global no Administrador do Commerce não define automaticamente esse grupo de clientes como &quot;*Negar*&quot; nas permissões da categoria.

<u>Pré-requisitos</u>:

* Instância B2B com um grupo de clientes definido e selecionado em **LOJAS** > **Configuração** > **CATÁLOGO** > **Catálogo** > **Permissões de categoria** para:
   * **Permitir Categoria de Navegação**
   * **Exibir preços do produto**
   * **Permitir adição ao carrinho**
* Em cada **Categoria**, o grupo de clientes é definido como &quot;*Permitir*&quot; para:
   * **Categoria de navegação**
   * **Exibir preços do produto**
   * **Adicionar ao carrinho**

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Commerce, acesse **LOJAS** > **Configuração** > **CATÁLOGO** > **Catálogo** > **Permissões de categoria** e desmarque o grupo de clientes de:
   * **Permitir Categoria de Navegação**
   * **Exibir preços do produto**
   * **Permitir adição ao carrinho**
1. Clique em **Salvar configuração** botão.
1. Aguarde a execução dos indexadores.
1. Examinar **CATÁLOGO** > **Categorias** > **Permissões de categoria**.

<u>Resultados esperados</u>:

**Permissões de categoria** será definido como &quot;*Negar*&quot; para todas as categorias do grupo de clientes.

<u>Resultados reais</u>:

Nenhuma alteração nas permissões de categoria para o grupo de clientes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.

Para saber mais sobre a funcionalidade da empresa B2B, consulte os seguintes artigos na documentação do desenvolvedor:

* [Guia do desenvolvedor B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gerenciar funções da empresa](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referência de caminhos de configuração da extensão B2B do Adobe Commerce Enterprise](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
