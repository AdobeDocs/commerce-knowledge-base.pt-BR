---
title: "MDVA-39482: o produto sai do estoque se importado com a quantidade '0' com ordens pendentes habilitadas"
description: O MDVA-39482 corrige o problema em que o produto sai do estoque se importado com a quantidade "0" quando o MSI e os backorders estão habilitados e o Limite de Indisponibilidade é definido como um valor menos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 está instalada. A ID do patch é MDVA-39482. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: o produto sai do estoque se importado com a quantidade &quot;0&quot; com ordens pendentes ativadas

O MDVA-39482 corrige o problema em que o produto sai do estoque se importado com a quantidade &quot;0&quot; quando o MSI e os backorders estão habilitados e o Limite de Indisponibilidade é definido como um valor menos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.1.4 está instalado. A ID do patch é MDVA-39482. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto fica indisponível se for importado com a quantidade &quot;0&quot; quando o MSI e os pedidos pendentes estiverem ativados e o Limite de indisponibilidade for definido como um valor menos.

<u>Pré-requisitos</u>:

1. O MSI e os dados de amostra devem ser instalados.
1. Ir para **Lojas** > **Configurações** > **Catálogo** > **Inventário**:
   * Definir Backorders para &quot;Permitir Qtd. Abaixo de 0&quot;
   * Definir limite de indisponibilidade para &quot;-10&quot;

<u>Etapas a serem reproduzidas</u>:

1. Verifique se o SKU está **Em estoque** e tem quantidade **24-MB01**.
1. Importe o CSV das origens de estoque. Certifique-se de selecionar &quot;Fontes de estoque&quot; em Tipo de entidade:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Verifique o status do estoque do produto após a importação das Fontes de estoque.

<u>Resultados esperados</u>:

24-MB01 é **Em estoque** na Loja.

<u>Resultados reais</u>:

24-MB01 é **Sem estoque** na Loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
