---
title: 'MDVA-42283: formato de data-hora para localidade francesa é inválido'
description: O patch MDVA-42283 corrige o problema em que o formato de data e hora na grade de pedido de administrador do local francês é inválido. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-42283. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 9b470e7b-4b73-4100-9a9d-1a45a5ac628b
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42283: Formato de data/hora para localidade francesa inválido

O patch MDVA-42283 corrige o problema em que o formato de data e hora na grade de pedido de administrador do local francês é inválido. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.13 está instalado. A ID do patch é MDVA-42283. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O formato de data e hora na grade do pedido de administração da localidade francesa é inválido.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma página de Pedido, Cliente, CMS ou Bloco de CMS.
1. Ir para **Admin** > **Configurações da conta** e defina a localidade da interface para admin **Français (Canadá)**/**français (Canadá)(fr_CA)** ou **Português do Brasil (pt_BR)**.
1. Observe o valor na coluna de data para qualquer ordem, remessa, aviso de crédito, cliente, página CMS ou grade de bloco CMS.

<u>Resultados esperados</u>:

A data está no formato exibido na página de edição real da entidade.

<u>Resultados reais</u>:

O valor de data e hora está incorreto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
