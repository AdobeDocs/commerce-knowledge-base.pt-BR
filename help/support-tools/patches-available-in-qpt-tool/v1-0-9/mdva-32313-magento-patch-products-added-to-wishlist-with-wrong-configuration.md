---
title: "Patch MDVA-32313: produtos adicionados à lista de desejos com configuração incorreta"
description: O patch MDVA-32313 resolve o problema em que os produtos configuráveis não podem ser adicionados à lista de desejos corretamente, porque recebem configurações incorretas quando são adicionados à lista de desejos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Correção do MDVA-32313: produtos adicionados à lista de desejos com configuração incorreta

O patch MDVA-32313 resolve o problema em que os produtos configuráveis não podem ser adicionados à lista de desejos corretamente, porque recebem configurações incorretas quando são adicionados à lista de desejos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.10 está instalado. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente.
1. Faça logon na conta do cliente.
1. Navegue até a **Lista de produtos** página.
1. Escolha um produto configurável (Exemplo: *configurável\_1* ) e selecione as opções de cor e tamanho preferenciais na **Lista de produtos** página (**Não abra a página do produto.**).
1. Clique no ícone da lista de desejos de outro produto configurável (Exemplo: *configurável\_2*) na mesma página sem selecionar opções de cor/tamanho.

<u>Resultados esperados</u>:

A variável *configurável\_2* o produto é adicionado à lista de desejos sem as opções selecionadas, conforme esperado.

<u>Resultados reais</u>:

A variável *configurável\_2* produto adicionado à lista de desejos com a configuração do *configurável\_1* produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
