---
title: "MDVA-38799: os produtos baixáveis não são salvos após a criação de uma atualização de preparo"
description: O patch MDVA-38799 resolve o problema em que os produtos baixáveis não são salvos após a criação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 está instalada. A ID do patch é MDVA-38799. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: Produtos baixáveis não salvos após a criação de uma atualização de preparo

O patch MDVA-38799 resolve o problema em que os produtos baixáveis não são salvos após a criação de uma atualização de preparo. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.0 está instalado. A ID do patch é MDVA-38799. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos baixáveis não são salvos após a criação de uma atualização de preparo. Os usuários recebem a mensagem de erro: *A amostra para download não está relacionada ao produto. Verifique o link e tente novamente*.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até **Catálogo** > **Produtos**.
1. Clique na lista suspensa ao lado de Adicionar produto e selecione Produto baixável.
   * Preencha o nome, SKU, preço e quantidade do produto.
1. Role para baixo até a página Informações baixáveis.
1. Em Amostras, clique em **Adicionar link**.
   * Preencha o Título, Fazer upload do arquivo (o tipo de arquivo não importa).
1. Clique em **Salvar**. Você receberá a seguinte mensagem: *Você salvou o produto*.
1. Clique em **Agendar nova atualização** na parte superior da página.
   * Preencha o Nome da atualização e uma Data de início e data de término válidas.
1. Clique em **Salvar** na atualização em preparo.
1. Clique em **Salvar** no produto.

<u>Resultados esperados</u>:

O produto é salvo sem erros.

<u>Resultados reais</u>:

Você receberá a mensagem de erro: *A amostra para download não está relacionada ao produto. Verifique o link e tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
