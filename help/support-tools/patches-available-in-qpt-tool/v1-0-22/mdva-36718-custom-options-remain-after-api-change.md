---
title: "MDVA-36718: as opções personalizadas permanecem após a alteração da API"
description: O patch MDVA-36718 Magento corrige o problema quando as opções personalizadas antigas permanecem após serem alteradas por meio da API.
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718: as opções personalizadas permanecem após a alteração da API

O patch MDVA-36718 Magento corrige o problema quando as opções personalizadas antigas permanecem após serem alteradas por meio da API.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.22 está instalado. A ID do patch é MDVA-36718. Observe que o problema está programado para ser corrigido na versão 2.4.3 do Magento.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Magento:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Adicionar um **tipo suspenso** opção personalizada.
1. Atualize a opção personalizada por meio da API: Enviar `PUT` solicitação para `/V1/products/options/{optionId}`.

<u>Resultados esperados</u>:

As opções personalizadas são atualizadas, conforme esperado.

<u>Resultados reais</u>:

Novas opções personalizadas são adicionadas, mas as antigas opções personalizadas permanecem.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique o problema de Magento com a Ferramenta de correção de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
