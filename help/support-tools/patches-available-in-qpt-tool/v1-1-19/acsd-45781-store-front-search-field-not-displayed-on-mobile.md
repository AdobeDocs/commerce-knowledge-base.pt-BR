---
title: "ACSD-45781: o campo de pesquisa frontal da loja não é exibido no celular"
description: O patch MDVA-45781 resolve o problema em que o campo de pesquisa frontal da loja não é exibido em dispositivos móveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 está instalada. A ID do patch é MDVA-45781. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 0ae90f6d-1c04-4599-b21d-4d02fd6b36db
feature: Cache, Native Luma Frontend Development, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-45781: O campo de pesquisa frontal da loja não é exibido no celular

O patch MDVA-45781 resolve o problema em que o campo de pesquisa frontal da loja não é exibido em dispositivos móveis. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.19 está instalado. A ID do patch é MDVA-45781. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O campo de pesquisa frontal da loja não é exibido em dispositivos móveis

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador do Commerce > **Lojas** > **Configuração** > **Catálogo** > **Pesquisa no catálogo** e defina:
   * Ativar o Search Recommendations para *Não*
   * Ativar sugestões de pesquisa para *Não*
1. Clique no link **Salvar configuração** botão.
1. Limpar cache.
1. Usando o tema Luma padrão, navegue com dispositivos móveis.
1. Clique no link **Pesquisar** botão.

<u>Resultados esperados</u>:

Formulário de pesquisa de entrada é exibido.

<u>Resultados reais</u>:

Nada acontece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
