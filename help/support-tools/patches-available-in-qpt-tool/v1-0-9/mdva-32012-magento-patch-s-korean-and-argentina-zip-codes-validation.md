---
title: "Patch MDVA-32012: validação de códigos postais dos EUA, Coreia e Argentina"
description: O patch MDVA-32012 resolve o problema em que os códigos postais da Argentina e da Coreia do Sul não estão sendo validados, devido a alterações ou variações nos formatos de código postal nacional. Os códigos postais da Coreia do Sul agora precisam ter 5 dígitos, enquanto anteriormente tinham 6 dígitos. Os códigos postais argentinos podem ser numéricos e alfanuméricos. A correção MDVA-32012 significa que esses formatos para valores de código postal serão validados para esses países. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.2.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Correção MDVA-32012: validação de códigos postais de S. Korean e Argentina

O patch MDVA-32012 resolve o problema em que os códigos postais da Argentina e da Coreia do Sul não estão sendo validados, devido a alterações ou variações nos formatos de código postal nacional. Os códigos postais da Coreia do Sul agora precisam ter 5 dígitos, enquanto anteriormente tinham 6 dígitos. Os códigos postais argentinos podem ser numéricos e alfanuméricos. A correção MDVA-32012 significa que esses formatos para valores de código postal serão validados para esses países. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.9 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.5.
* O patch também é compatível com as seguintes versões do Adobe Commerce: Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A inserção de códigos postais sul-coreanos ou argentinos alfanuméricos de 5 dígitos produz um aviso:

*O CEP fornecido parece ser inválido. Exemplo: [1234 (se inserido um endereço alfanumérico argentino)] ou [123-456 (se inserido um endereço de 5 dígitos em coreano)]. Se você acredita que é o correto, você pode ignorar este aviso.*

<u>Etapas a serem reproduzidas</u>:

1. Abra a loja.
1. Adicionar item ao carrinho.
1. Processo para finalização.
1. Adicione um novo endereço com a Coreia do Sul para o país e insira um CEP de 5 dígitos ou adicione um novo endereço com a Argentina para o país e insira um CEP alfanumérico.
1. Tente salvar.

<u>Resultados esperados</u>:

O endereço deve ser salvo sem aviso.

<u>Resultados reais</u>:

Salvar endereço retorna um aviso.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
