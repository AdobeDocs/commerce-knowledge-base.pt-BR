---
title: Como obter e aplicar o [!UICONTROL security patch]
description: Este artigo fornece instruções sobre como obter e aplicar um [!UICONTROL security patch] que foi lançado, mas as instruções não estão disponíveis.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 43c8308c6539c53f60fb6457047898a2edd46532
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Como obter e aplicar um [!UICONTROL security patch]

>[!NOTE]
>Se você tiver uma instalação no local e não estiver usando sistemas de controle de versão como o [!DNL CVS] ou o [!DNL GitHub] para gerenciar seu código, talvez o host da Web possa ajudá-lo a aplicar o patch. Entre em contato com eles para obter suporte

Este artigo fornece instruções sobre como obter e aplicar um [!UICONTROL security patch] que foi lançado, mas as instruções não estão disponíveis.

## Produtos e versões afetados

Adobe Commerce no local e na nuvem - Todas as versões


## Causa

A maioria dos [!UICONTROL Security Patches] foi lançada sem nenhum patch ou hotfix isolado para ser aplicada e exigirá atualização para a versão [!UICONTROL Security Patch].

## Solução


### Caso I:

* Se um arquivo/hotfix de patch isolado for mencionado nas [Notas de Versão](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite), baixe o arquivo da seção de download de [https://account.magento.com](https://account.magento.com/downloads/view/). Os usuários com acesso compartilhado devem primeiro receber privilégios de download do proprietário da conta/titular da licença.

**Avisos:**

Se você estiver em uma versão mais antiga do Adobe Commerce (2.4.4), terá recebido automaticamente o Suporte estendido. Sua versão deve ser uma das seguintes versões não suportadas para poder aplicar os patches de segurança mais recentes disponíveis:

2.4.4 - 2.4.4-p11

Versões não compatíveis (2.3.x, 2.4.0 - 2.4.3) não são elegíveis para suporte e você deve primeiro atualizar para uma versão compatível para aproveitar as correções de segurança mais recentes.

Se você não tiver o suporte estendido, poderá solicitar suporte para compartilhar os patches com você, mas eles não poderão resolver nenhum problema/erro que você possa encontrar ao aplicá-los.

### Caso II:

Os patches isolados são fornecidos apenas em casos excepcionais, e não é a forma preferida de implementar correções de segurança.

Se um arquivo/hotfix de patch isolado não for mencionado nas Notas de versão:

* **Nuvem:**

1. Alguns [!UICONTROL Security Patches] podem ser incluídos/lançados na versão mais recente do Conjunto de ferramentas da nuvem (Ferramentas ECE) em Patches da nuvem para o Commerce - verifique as [Notas de versão](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) e, se uma correção de segurança for mencionada na versão, atualize o pacote para essa versão.
1. Se as Notas de versão não mencionarem uma correção de segurança, continue lendo.

* **Nuvem ou no Local:**

* Se um arquivo/hotfix de patch isolado não estiver disponível, [atualize a versão do Adobe Commerce na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X para a versão de patch mais recente 2.4.X-pY.
* Se um arquivo/hotfix de patch isolado não estiver disponível, [atualize a versão do Adobe Commerce no local](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X para a versão de patch mais recente 2.4.X-pY.

## Leitura relacionada

* Consulte as [Notas de versão do Conjunto de ferramentas do Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) no *Guia de Infraestrutura do Adobe Commerce na Nuvem*.
* Consulte [Atualizar a versão do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) no *Guia de Infraestrutura do Adobe Commerce on Cloud*.
