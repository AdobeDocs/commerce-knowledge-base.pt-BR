---
title: "MDVA-39711: Não é possível acessar a grade dos clientes após excluir o site"
description: O patch MDVA-39711 corrige o problema em que o usuário administrador não consegue acessar a grade do cliente após excluir o site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. A ID do patch é MDVA-39711. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 46bef304-9360-4b69-b064-631725de381c
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-39711: Não é possível acessar a grade dos clientes após excluir o site

O patch MDVA-39711 corrige o problema em que o usuário administrador não consegue acessar a grade do cliente após excluir o site. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. A ID do patch é MDVA-39711. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7-p2, 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode acessar a grade dos clientes após excluir o site.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo site, loja e exibição de loja.
1. Crie um novo cliente no Administrador e associe-o ao site criado.
1. Vá para **Lojas** > **Todas as lojas** e exclua o site criado.
1. Vá para **Clientes** > **Todos os clientes**.

<u>Resultados esperados</u>:

* Não há mensagem de erro.
* Todos os clientes estão visíveis na grade.

<u>Resultados reais</u>:

* O usuário recebe uma mensagem de erro: *O site com a ID 2 solicitada não foi encontrado. Verifique o site e tente novamente*
* Nenhum cliente é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
