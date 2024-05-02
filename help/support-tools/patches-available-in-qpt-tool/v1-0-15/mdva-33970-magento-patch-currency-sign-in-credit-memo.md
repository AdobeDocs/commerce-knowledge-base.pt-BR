---
title: "Correção MDVA-33970: sinal de moeda no memorando de crédito"
description: O patch MDVA-33970 resolve o problema em que um sinal de dólar ($) era exibido em vez da moeda localizada em um memorando de crédito. Isso ocorre quando um escopo **Site** é usado para um atributo **Preço**.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Correção do MDVA-33970: sinal de moeda no memorando de crédito

O patch MDVA-33970 resolve o problema em que um sinal de dólar ($) era exibido em vez da moeda localizada em um memorando de crédito. Isso ocorre quando um **Site** o escopo é usado para um **Preço** atributo.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.15 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-condições</u>:

Neste exemplo, as seguintes configurações são usadas:

* Existem 2 sites - cada um tem um **Loja** e uma **Exibição da loja**.
* A variável **Configuração padrão** tem o Dólar de Singapura como **Moeda** (**Lojas > Configuração > Geral > Configuração de Moeda**):
   * **Moeda de base** = *Dólar de Singapura*
   * **Moeda de Exibição Padrão** = *Dólar de Singapura*
   * **Moedas permitidas** = *Dólar de Singapura*
* **Site 1** tem um **Configuração padrão**.
* **Site 2** tem o Ringgit malaio como **Moeda**:
   * **Moeda de base** = *Ringgit malaio*
   * **Moeda de Exibição Padrão** = *Ringgit malaio*
   * **Moedas permitidas** = *Ringgit malaio*
* Ir para **Lojas > Símbolos de Moeda**, e Defina:
   * **MYR (Ringgit malaio)** = *RM*
   * **SGD (Dólar de Singapura)** = *SGD* (**Usar Padrão** = *Marcado*)
* Alguns **Produto** existe.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **Pedido** do **Site 2** (você pode configurá-lo como Padrão para evitar configurações adicionais).
1. Fazer logon em **Admin**.
1. Abra o pedido recém-criado.
1. Verifique se **Símbolo de moeda** = *RM*.
1. Criar um **Fatura**.
1. Verifique se **Símbolo de moeda** = *RM* na fatura.
1. Criar um **Aviso de Crédito**.
1. Verifique se **Símbolo de moeda**  ** ** = *RM* no **Aviso de Crédito**.
1. Abra o **Avisos de Crédito** guia em **Pedido**.
1. Verifique a **Símbolo de moeda** na grade.
1. Abertura **Vendas > Avisos de Crédito**.
1. Verifique a **Símbolo de moeda** na grade.

<u>Resultados esperados</u>:

O símbolo de moeda localizado correto é usado, conforme esperado.

<u>Resultados reais</u>:

O cifrão ($) é usado, mesmo que não esteja configurado nas configurações de Administração.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
