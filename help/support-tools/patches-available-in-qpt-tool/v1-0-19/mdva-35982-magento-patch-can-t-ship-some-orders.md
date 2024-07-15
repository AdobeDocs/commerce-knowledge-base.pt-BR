---
title: "MDVA-35982: não é possível enviar alguns pedidos"
description: O patch MDVA-35982 corrige o erro quando o usuário administrador restrito a um site específico não pode criar uma remessa para o pedido feito no mesmo site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35982. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: Não é possível enviar alguns pedidos

O patch MDVA-35982 corrige o erro quando o usuário administrador restrito a um site específico não pode criar uma remessa para o pedido feito no mesmo site. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35982. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O comerciante não pode enviar determinados pedidos.

<u>Etapas a serem reproduzidas</u>:

1. Escolha qualquer site do produto para o produto, exceto a loja padrão. Consulte [Produto em Sites](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) no guia do usuário para ver as etapas detalhadas.
1. Crie uma função de usuário para o Administrador com escopos de função personalizados, na qual o site/armazenamento padrão não esteja selecionado. Consulte [Definir uma função](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) no guia do usuário para ver as etapas detalhadas.
1. Abra o produto no modo de edição e defina um Preço de Grupo para esse produto, no **Advanced Pricing**. Consulte [Preço em grupo](https://docs.magento.com/user-guide/catalog/product-price-group.html) em nosso guia do usuário para ver as etapas detalhadas.
1. Criar um pedido com este produto.
1. Faça logon como Administrador com essa função de usuário e crie uma remessa. Consulte [Criando uma Remessa](https://docs.magento.com/user-guide/sales/shipments-create.html) em nosso guia do usuário para obter etapas detalhadas.

<u>Resultados esperados</u>:

A remessa é criada.

<u>Resultados reais</u>:

O seguinte erro é exibido:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
