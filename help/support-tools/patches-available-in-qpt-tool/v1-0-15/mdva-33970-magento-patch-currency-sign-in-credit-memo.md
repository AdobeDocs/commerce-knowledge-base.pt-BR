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

O patch MDVA-33970 resolve o problema em que um sinal de dólar ($) era exibido em vez da moeda localizada em um memorando de crédito. Isso ocorre quando um escopo do **Site** é usado para um atributo de **Preço**.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem e Adobe Commerce no local 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-condições</u>:

Neste exemplo, as seguintes configurações são usadas:

* Existem 2 sites - cada um tem uma **Loja** e uma **Exibição de Loja**.
* A **Configuração Padrão** tem o Dólar de Singapura como **Moeda** (**Lojas > Configuração > Geral > Configuração de Moeda**):
   * **Moeda Base** = *Dólar de Singapura*
   * **Moeda de Exibição Padrão** = *Dólar de Singapura*
   * **Moedas Permitidas** = *Dólar de Singapura*
* O **Site 1** tem uma **Configuração Padrão**.
* **O site 2** tem o Ringgit malaio como **Moeda**:
   * **Moeda Base** = *Ringgit Malaio*
   * **Moeda de Exibição Padrão** = *Ringgit Malaio*
   * **Moedas Permitidas** = *Ringgit Malaio*
* Vá para **Lojas > Símbolos de Moeda** e Defina:
   * **MYR (Ringgit malaio)** = *RM*
   * **SGD (Dólar de Singapura)** = *SGD* (**Usar Padrão** = *Verificado*)
* Algum **Produto** existe.

<u>Etapas a serem reproduzidas</u>:

1. Fazer um **Pedido** do **Site 2** (você pode configurá-lo como Padrão para evitar configurações adicionais).
1. Faça logon em **Admin**.
1. Abra o pedido recém-criado.
1. Verifique se o **Símbolo de Moeda** = *RM*.
1. Criar uma **Fatura**.
1. Verifique se o **Símbolo de Moeda** = *RM* está na fatura.
1. Crie um **Aviso de Crédito**.
1. Verifique se o **Símbolo de Moeda** ** ** = *RM* no **Memorando de Crédito**.
1. Abra a guia **Avisos de Crédito** em **Ordem**.
1. Verifique o **Símbolo de Moeda** na grade.
1. Abra **Vendas > Avisos de Crédito**.
1. Verifique o **Símbolo de Moeda** na grade.

<u>Resultados esperados</u>:

O símbolo de moeda localizado correto é usado, conforme esperado.

<u>Resultados reais</u>:

O cifrão ($) é usado, mesmo que não esteja configurado nas configurações de Administração.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
