---
title: "MDVA-38666: o usuário administrador não pode alterar as opções de produto configuráveis"
description: O patch MDVA-38666 resolve o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-38666. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: O usuário administrador não pode alterar as opções de produto configuráveis

O patch MDVA-38666 resolve o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.9 está instalado. A ID do patch é MDVA-38666. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Definir escopo da conta do cliente como Global.
1. Crie dois sites com lojas.
1. Crie dois produtos configuráveis e atribua-os a cada site.
1. Crie uma conta do cliente no front-end e faça logon.
1. Adicione um produto ao carrinho e faça uma finalização (isso é feito para tornar as IDs de cotação diferentes em cada site).
1. Adicione um produto ao carrinho e deixe-o.
1. Alterne para o segundo site e adicione o produto ao carrinho (o mesmo logon deve funcionar, pois o escopo da conta do cliente está definido como Global).
1. Abra o cliente no admin e navegue até a guia do carrinho.
1. Alterne o armazenamento do menu suspenso e tente alterar a configuração.

<u>Resultados esperados</u>:

O usuário recebe um pop-up com opções configuráveis.

<u>Resultados reais</u>:

Nenhum formulário pop-up é exibido. O usuário não pode alterar a configuração.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
