---
title: "ACSD-45255: Exceção na página de relatório de Baixo Estoque para usuário administrador restrito"
description: O patch ACSD-45255 resolve o problema em que uma exceção é lançada na página Relatório de baixo estoque para um usuário administrador restrito. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-45255. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 4b08500a-384e-4d5b-9563-3f9d1b984349
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-45255: Exceção na página de relatório de Baixo Estoque para usuário administrador restrito

O patch ACSD-45255 resolve o problema em que uma exceção é lançada na página Relatório de baixo estoque para um usuário administrador restrito. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.18 está instalado. A ID do patch é ACSD-45255. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma exceção é lançada na página Relatório de baixo estoque para um usuário administrador restrito.

<u>Pré-requisitos</u>:

* Os módulos de inventário estão habilitados.
* Há um site adicional, loja e visualização de loja.
* Há um usuário administrador restrito com acesso somente ao site adicional.

<u>Etapas a serem reproduzidas</u>:

1. Abra o Administrador do Commerce como o usuário administrador restrito.
1. Ir para **Relatórios** > **Produtos** > **Baixo Estoque**.

<u>Resultados esperados</u>:

O relatório Baixo estoque é exibido para o usuário administrador restrito.

<u>Resultados reais</u>:

Uma exceção é lançada:

```bash
TypeError: Argument 1 passed to Magento\InventoryLowQuantityNotification\Model\ResourceModel\LowQuantityCollection\Interceptor::addStoreFilter() must be of the type int, array given, called in ../app/code/Magento/AdminGws/Plugin/CollectionFilter.php on line 101 and defined in ../generated/code/Magento/InventoryLowQuantityNotification/Model/ResourceModel/LowQuantityCollection/Interceptor.php:20
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
