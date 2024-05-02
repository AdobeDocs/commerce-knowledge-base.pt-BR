---
title: "MDVA-42689: os usuários obtêm erro de violação de restrição de integridade ao atualizar categorias de produto durante a importação"
description: O patch MDVA-42689 resolve o problema em que os usuários recebem um erro de violação de restrição de integridade ao atualizar categorias de produtos durante a importação. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42689. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 7beff3bb-9313-43dc-be96-e33eff52a38e
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-42689: Os usuários obtêm o erro Violação de Restrição de Integridade ao atualizar categorias do produto durante a importação

O patch MDVA-42689 resolve o problema em que os usuários recebem um erro de violação de restrição de integridade ao atualizar categorias de produtos durante a importação. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.12 está instalado. A ID do patch é MDVA-42689. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Adobe Commerce lança um erro de violação de restrição de integridade ao atualizar categorias de produto durante a importação.

<u>Etapas a serem reproduzidas</u>:

1. Configure dois sites.
1. Crie subcategorias na categoria raiz até dois níveis na página de categoria. Por exemplo, Categoria raiz > **Engrenagem** > **Relógios**.
1. Criar dois produtos simples e atribuir ambos aos mesmos **Engrenagem** > **Relógios** categoria.
1. Atribua um produto simples aos dois sites.
1. Salve o produto.
1. Prepare um arquivo CSV para importação. Deve haver dois registros de produto com visualizações de loja diferentes. Um dos produtos deve pertencer a essas duas visualizações da loja.
1. Agora importe o arquivo CSV navegando até **Sistema** > **Importar** > **Tipo de entidade** (Produtos).

<u>Resultados esperados</u>:

O arquivo CSV é importado sem erros.

<u>Resultados reais</u>:

O Adobe Commerce emite o seguinte erro:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
