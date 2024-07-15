---
title: 'MDVA-34850: amostras sem inventário tachado atingem "0"'
description: O patch MDVA-34850 corrige o problema em que as amostras não são atingidas quando o inventário atinge "0" e não estão visíveis no link da Página de detalhes do produto (PDP) para nenhuma outra amostra do In-Stock. O **Exibir produtos indisponíveis** também está definido como *Sim* na configuração do administrador. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: amostras sem inventário tachado atingem &quot;0&quot;

O patch MDVA-34850 corrige o problema em que as amostras não são atingidas quando o inventário atinge &quot;0&quot; e não estão visíveis no link da Página de detalhes do produto (PDP) para nenhuma outra amostra do In-Stock. A **Exibir Produtos Indisponíveis** também está definida como *Sim* na configuração do administrador. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.1 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As opções de Produto indisponível não são exibidas na página PDP quando o estoque de estoque padrão não está em uso e a configuração **Exibir Produtos Indisponíveis** está habilitada.

<u>Pré-requisitos</u>:

* Instale o Multi-Source Inventory (MSI).
* Habilitar Exibir Produtos Indisponíveis em [Opções de Estoque de Estoque](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).

<u>Etapas a serem reproduzidas</u>:

1. Criar novo estoque de estoque \[Novo estoque\], atribuindo todos os sites a ele e à origem acima. Agora, o estoque padrão não deve estar em uso.
1. Crie um [produto configurável](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) adicionando três opções de tamanho \[S,M,L\].
1. Abra cada opção e adicione quantidades atribuindo somente a origem personalizada \[new\_source\] criada. Além disso, defina \[Status do Source\] como \[No Stock\].
1. Reindexe e verifique o produto configurável no front-end. Todas as três opções devem estar visíveis.
1. Abra um produto simples atribuído a \[size:S\] no back-end e defina o \[Status do Source\] como \[Fora do Estoque\] e atualize também a quantidade como 0. Reindexe e verifique o produto configurável no front-end.

<u>Resultados esperados</u>:

Como a opção Exibir produtos indisponíveis está ativada, todas as três opções devem ser exibidas. A opção Out-of-Stock \[S\] deve ser desativada e riscada. Ele deve exibir 2 x de 1 produto opcional com preço = 12x2 para obter detalhes sobre o front-end e o back-end.

<u>Resultados reais</u>:

A opção Out-of-Stock está oculta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
