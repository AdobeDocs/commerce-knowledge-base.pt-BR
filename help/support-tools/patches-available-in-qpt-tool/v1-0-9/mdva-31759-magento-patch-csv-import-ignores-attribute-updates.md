---
title: "Patch MDVA-31759: a importação de CSV ignora atualizações de atributo"
description: O patch MDVA-31759 corrige o problema em que a importação de CSV ignora atributos adicionais com os tipos *Suspenso* e *Área de texto*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Patch MDVA-31759: a importação de CSV ignora atualizações de atributo

O patch MDVA-31759 corrige o problema em que a importação de CSV ignora atributos adicionais com tipos *Suspenso* e *Área de Texto*. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A importação de CSV ignora atributos adicionais com *Lista suspensa* e *Área de Texto* tipos.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce.
1. Crie um atributo de produto com a seguinte configuração:
   * **Rótulo Padrão**: *G003*
   * **Tipo de Entrada de Catálogo para o Proprietário da Loja**: *Área de Texto* ou *Lista Suspensa*
   * **Código de Atributo**: *G003*
   * **Escopo**: *Global*
1. Adicione o atributo acima ao conjunto de atributos padrão.
1. Crie um produto com o atributo padrão definido e especifique um valor para o novo atributo.
1. Exporte o produto para CSV.
1. Atualize o valor do atributo na coluna **additional\_attributes**.
1. Importe o CSV atualizado.

<u>Resultados esperados</u>:

O valor do atributo G003 é atualizado.

<u>Resultados reais</u>:

O valor do atributo G003 não foi atualizado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
