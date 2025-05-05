---
title: Patches disponíveis na visão geral da ferramenta QPT
description: Este artigo fornece uma visão geral do  [!DNL Quality Patches Tool] (QPT) e links para recursos que explicam como usá-lo.
exl-id: ac1c6088-44fe-452c-a39b-3c35697e1cc3
feature: Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Patches disponíveis na visão geral da ferramenta QPT

Este artigo fornece uma visão geral do [!DNL Quality Patches Tool] (QPT) e links para recursos que explicam como usá-lo.

## Produtos e versões afetados

* Adobe Commerce local, todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## O que é a Ferramenta de correção de qualidade?

O [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT) é uma ferramenta que permite aplicar patches de qualidade individuais desenvolvidos pelo Adobe e pela comunidade Magento Open Source.

Ele permite:

* aplicar patches de qualidade incluídos no pacote
* reverter patches aplicados anteriormente
* veja as informações gerais sobre patches de qualidade disponíveis para a versão instalada do Adobe Commerce.

Este é um exemplo da tabela de status que você pode obter para visualizar os patches disponíveis:

![Magento_patches_list](assets/status_table.png)

A ferramenta tem como objetivo permitir que você faça o autoatendimento com patches para problemas que possam ocorrer com o Adobe Commerce ou aplique facilmente patches sugeridos pelo suporte da Adobe Commerce.

>[!NOTE]
>
>O QPT é apenas para correções de qualidade. Os patches de segurança estão disponíveis nas [Notas de versão para Adobe Commerce e Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html?lang=pt-BR).

## Patches disponíveis no [!DNL Quality Patches Tool]

Nesta seção da Base de conhecimento de suporte da Adobe Commerce, você encontrará descrições detalhadas dos problemas, resolvidos por patches QPT, agrupados por versão de lançamento QPT.
Você também pode ver uma lista de patches QPT disponíveis e filtrar o por componente, usando a tabela gerada dinamicamente na [[!DNL Quality Patches Tool]: página Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) em nossa base de dados de conhecimento de suporte.

## Como instalar e usar o [!DNL Quality Patches Tool]

Os comandos de instalação e uso são diferentes para o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem, porque para a nuvem o pacote QPT está incluído no pacote ece-tools.

### Como instalar e usar o QPT para Adobe Commerce no local

Consulte [Commerce > Ferramentas > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) em nossa documentação do desenvolvedor para obter detalhes sobre como instalar e usar o QPT para aplicar e reverter patches.

### Como instalar e usar o QPT para Adobe Commerce na infraestrutura em nuvem

Consulte o [Guia de Infraestrutura do Commerce na Nuvem > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) em nossa documentação do desenvolvedor para obter detalhes sobre como instalar e usar o QPT para aplicar e reverter patches na infraestrutura na nuvem do Adobe Commerce.

## Leitura relacionada

* [[!DNL Quality Patches Tool] notas de versão](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=pt-BR) em nossa documentação para desenvolvedores.
