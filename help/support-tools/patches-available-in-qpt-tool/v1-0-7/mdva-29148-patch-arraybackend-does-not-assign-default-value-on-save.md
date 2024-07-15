---
title: "MDVA-29148: ArrayBackend não atribui valor padrão ao salvar"
description: O patch MDVA-29148 resolve o problema em que "\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend" não atribui o valor padrão ao salvar. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend não atribui o valor padrão ao salvar

O patch MDVA-29148 resolve o problema em que `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` não atribui o valor padrão ao salvar. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.3-p1.

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando um produto é criado por meio de um script de importação ou da API REST, os atributos que usam o modelo de back-end `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` e têm um valor padrão não recebem o valor padrão.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo atributo global que use o modelo de back-end `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` e um valor padrão não vazio.
1. Use a REST API para criar um novo produto.
1. Procure esse novo produto na REST API e confirme se o atributo não está presente nos atributos personalizados do produto.

<u>Resultados esperados</u>:

O valor padrão do atributo personalizado foi salvo no atributo do produto.

<u>Resultados reais</u>:

O valor padrão do atributo personalizado não foi salvo no atributo do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
