---
title: "MDVA-29787: os produtos relacionados não são exibidos"
description: O patch MDVA-29787 resolve o problema em que os **Produtos relacionados** não são exibidos no front-end de uma loja da Adobe Commerce. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. A ID do patch é MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: os produtos relacionados não são exibidos

O patch MDVA-29787 resolve o problema em que os **Produtos Relacionados** não são exibidos em um front-end de loja da Adobe Commerce. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada. A ID do patch é MDVA-29787.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.3.

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.0.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de destino para **Produtos Relacionados** não funciona quando a condição &quot;*is one of*&quot; é usada para **Produtos para Exibição** no Administrador do Commerce.

>[!NOTE]
>
>Observação: Este patch não corrige as regras de destino existentes. Você deve recriar as regras de destino existentes.

<u>Etapas a serem reproduzidas</u>:

1. Criar **Novo Atributo** (Exemplo: Test\_Attr).
   * Definir **Tipo de Entrada de Catálogo para o Proprietário do Repositório** = *Texto.*
   * Em **Propriedades da vitrine**, defina **Usar para Condições de Regra Promo** = *Sim*.
1. Criar **Novo Conjunto De Atributos** (Exemplo: Test\_Set).
1. Adicionar o **Novo Atributo** ao **Novo Conjunto de Atributos** (Exemplo: Adicionar o atributo &quot;Test\_Attr&quot; ao conjunto de atributos &quot;Test\_Set&quot;).
1. Crie três produtos. Por exemplo, elas são definidas assim:
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Produto3, Teste\_Attr = 701644329389M
1. Criar **Regra** de destino (**Marketing**)   > **Regras de Produto Relacionadas** e clique no botão **Adicionar Regra**.) com configurações:
   * **Aplicar A** = *Produtos Relacionados*
   * **Produtos correspondentes**
   * Defina o Novo Atributo que você criou **em** **Etapa 1 acima** para ser o atributo Product1 (Exemplo: Test\_Attr = MAGT2NA\_Test3).
   * **Produtos a Serem Exibidos** = Os atributos dos outros dois produtos (Exemplo: 24-MB02 e 701644329389M atributos).
1. Salve a **Regra**.
1. Execute uma reindexação, se necessário.
1. Limpar cache.
1. Abra o Product1 no front-end.

<u>Resultados esperados</u>:

Os produtos relacionados estão presentes.

<u>Resultados reais</u>:

Os produtos relacionados estão ausentes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
