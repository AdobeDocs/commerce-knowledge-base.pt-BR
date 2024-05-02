---
title: "MDVA-41061: O status do estoque é redefinido para vendável quando o produto é salvo do Administrador"
description: O patch MDVA-41061 corrige o problema em que o status do estoque é redefinido para vendable quando o produto é salvo do Admin. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 está instalada. A ID do patch é MDVA-41061. A versão de patch mais recente está disponível no QPT 1.1.15 com ID de patch MDVA-41061-V3. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: O status do estoque é redefinido para vendável quando o produto é salvo do Administrador

O patch MDVA-41061 corrige o problema em que o status do estoque é redefinido para vendable quando o produto é salvo do Admin. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.1.5 está instalado. A ID do patch é MDVA-41061. A versão de patch mais recente está disponível no QPT 1.1.15 com ID de patch MDVA-41061-V3. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque é redefinido para vendável quando o produto é salvo do Administrador.

<u>Pré-requisitos</u>:

Os módulos de inventário estão instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com Qtd. = 1.
1. Faça um pedido usando o produto criado na etapa 1.
1. Execute cron - certifique-se `inventory.reservations.updateSalabilityStatus` fila é executada e o status do estoque do produto foi alterado para zero na variável `cataloginventory_stock_status` tabela.
1. Verifique o produto no front-end. Deve ser marcado como **Sem estoque**.
1. Salve o produto no Administrador sem nenhuma alteração.

<u>Resultados esperados</u>:

* O status do estoque não deve ser atualizado.
* O produto deve ser **Sem estoque** no front-end.

<u>Resultados reais</u>:

* O produto simples está marcado como **Em estoque** no front-end.
* Os usuários obtêm *A quantidade solicitada não está disponível* ao tentar adicioná-la ao carrinho.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
