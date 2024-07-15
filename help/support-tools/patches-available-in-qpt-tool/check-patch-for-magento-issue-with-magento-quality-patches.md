---
title: Verifique o problema do Adobe Commerce com a Ferramenta de correções de qualidade
description: Este artigo fornece uma visão geral da Ferramenta de correções de qualidade (QPT) e links para recursos que explicam como usá-la.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Verifique o problema do Adobe Commerce com a Ferramenta de correções de qualidade

Este artigo fornece uma visão geral da Ferramenta de correções de qualidade (QPT) e links para recursos que explicam como usá-la.

## Produtos e versões afetados

* Adobe Commerce local, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## O que são a Ferramenta de correção de qualidade

A [Ferramenta de Patches de Qualidade](https://github.com/magento/quality-patches) (QPT) são patches individuais desenvolvidos pela Adobe e pela comunidade Magento Open Source.

Ele permite:

* aplicar patches de qualidade incluídos no pacote
* reverter patches aplicados anteriormente
* veja as informações gerais sobre patches de qualidade disponíveis para a versão instalada do Adobe Commerce.

Este é um exemplo da tabela de status que você pode obter para visualizar os patches disponíveis:

![Magento_patches_list](assets/status_table.png)

A ferramenta tem como objetivo permitir que você faça o autoatendimento com patches para problemas que possam ocorrer com o Adobe Commerce ou aplique facilmente patches sugeridos pelo suporte da Adobe Commerce.

>[!NOTE]
>
>O QPT é apenas para correções de qualidade. Os patches de segurança estão disponíveis na [Central de Segurança do Magento](https://magento.com/security/patches).

## Patches disponíveis na Ferramenta de patches de qualidade

Consulte a [Ferramenta de Patches de Qualidade](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) em nossa documentação do desenvolvedor para obter a lista de patches disponíveis.

## Como instalar e usar a Ferramenta de correções de qualidade

Os comandos de instalação e uso são diferentes para o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem, porque para a nuvem o pacote QPT está incluído no pacote ece-tools.

### Como instalar e usar o QPT para Adobe Commerce no local

Consulte o [Guia de Atualização de Software > Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) em nossa documentação do desenvolvedor para obter detalhes sobre como instalar e usar o QPT para aplicar e reverter patches.

### Como instalar e usar o QPT para Adobe Commerce na infraestrutura em nuvem

Consulte [Nuvem para Adobe Commerce > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) em nossa documentação do desenvolvedor para obter detalhes sobre como instalar e usar o QPT para aplicar e reverter patches no Adobe Commerce na infraestrutura em nuvem.

## Leitura relacionada

* [Notas de versão da Ferramenta de correções de qualidade](https://devdocs.magento.com/quality-patches/release-notes.html) em nossa documentação do desenvolvedor.
* [Como aplicar os patches do compositor fornecidos pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.
