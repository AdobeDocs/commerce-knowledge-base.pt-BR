---
title: 'MDVA-42689: Os usuários obtêm o erro Violação de Restrição de Integridade ao atualizar categorias do produto durante a importação'
description: O patch MDVA-42689 resolve o problema em que os usuários recebem um erro de violação de restrição de integridade ao atualizar categorias de produtos durante a importação. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42689. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 7beff3bb-9313-43dc-be96-e33eff52a38e
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-42689: Os usuários obtêm o erro Violação de Restrição de Integridade ao atualizar categorias do produto durante a importação

O patch MDVA-42689 resolve o problema em que os usuários recebem um erro de violação de restrição de integridade ao atualizar categorias de produtos durante a importação. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42689. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Adobe Commerce lança um erro de violação de restrição de integridade ao atualizar categorias de produto durante a importação.

<u>Etapas a serem reproduzidas</u>:

1. Configure dois sites.
1. Crie subcategorias na categoria raiz até dois níveis na página de categoria. Por exemplo, Categoria raiz > **Engrenagem** > **Observações**.
1. Crie dois produtos simples e atribua os dois à mesma categoria **Engrenagem** > **Inspeções**.
1. Atribua um produto simples aos dois sites.
1. Salve o produto.
1. Prepare um arquivo CSV para importação. Deve haver dois registros de produto com visualizações de loja diferentes. Um dos produtos deve pertencer a essas duas visualizações da loja.
1. Importe agora o arquivo CSV navegando para **Sistema** > **Importar** > **Tipo de Entidade** (Produtos).

<u>Resultados esperados</u>:

O arquivo CSV é importado sem erros.

<u>Resultados reais</u>:

O Adobe Commerce emite o seguinte erro:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
