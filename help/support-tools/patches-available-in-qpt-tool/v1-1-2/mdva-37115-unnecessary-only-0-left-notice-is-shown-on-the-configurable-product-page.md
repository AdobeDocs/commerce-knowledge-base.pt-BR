---
title: 'MDVA-37115: o aviso "Somente 0 restante" é exibido na página do produto'
description: O patch MDVA-37115 resolve o problema em que o aviso *Only 0 left* desnecessário é mostrado na página do produto configurável. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-37115. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 08aa6ac7-13ae-44c1-9db4-d449c3d8c985
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-37115: o aviso &quot;Apenas 0 restante&quot; é exibido na página do produto

O patch do MDVA-37115 resolve o problema em que a falha *Apenas 0 restantes* esse aviso é exibido na página do produto configurável. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.2 está instalado. A ID do patch é MDVA-37115. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os tipos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os tipos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um *Apenas 0 restantes* o aviso é exibido na página do produto configurável.

<u>Pré-requisitos</u>:

Os módulos de inventário estão instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com poucas opções.
1. Vá para o front-end.
1. Abra a página do produto configurável e selecione qualquer opção.

<u>Resultados esperados</u>:

Não *Apenas 0 restantes* O aviso é exibido na página do produto.

<u>Resultados reais</u>:

*Apenas 0 restantes* O aviso é exibido na página do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
