---
title: Como obter e aplicar [!UICONTROL security patch]
description: Este artigo fornece instruções sobre como obter e aplicar uma [!UICONTROL security patch] que foi lançado, mas as instruções não estão disponíveis.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Como obter e aplicar uma [!UICONTROL security patch]

Este artigo fornece instruções sobre como obter e aplicar uma [!UICONTROL security patch] que foi lançado, mas as instruções não estão disponíveis.

## Produtos e versões afetados

Adobe Commerce no local e na nuvem - Todas as versões

## Causa

Mais [!UICONTROL Security Patches] são lançados sem nenhum arquivo físico ou hotfix para serem aplicados.

## Solução


### Caso I:

Se um arquivo/hotfix de patch físico for mencionado nas Notas de versão:

* Baixe o arquivo na seção de download de [https://account.magento.com](https://account.magento.com/downloads/view/). (Os usuários com acesso compartilhado devem primeiro receber privilégios de download do proprietário da conta/titular da licença)

**Avisos:**

Se você estiver usando uma versão mais antiga do Adobe Commerce e tiver adquirido o Extended Support, sua versão deverá ser uma das seguintes para poder aplicar os patches de segurança:

* 2.4.2-p2
* 2.4.3-p3

Se você não tiver o suporte estendido, poderá solicitar suporte para compartilhar os patches com você, mas eles não poderão resolver nenhum problema/erro que você possa encontrar ao aplicá-los.

### Caso II:

Se um arquivo/hotfix de patch físico não for mencionado nas Notas de versão:

* **Nuvem:**

1. Alguns [!UICONTROL Security Patches] pode ser incluído/lançado na versão mais recente do Cloud Tools Suite (Ferramentas ECE) em Cloud Patches para Commerce - verifique a [Notas de versão](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)e se uma correção de segurança for mencionada na versão, atualize o pacote para essa versão.
1. Se as Notas de versão não mencionarem uma correção de segurança, continue lendo.

* **Nuvem ou no local:**

* Se um arquivo/hotfix de patch físico não estiver disponível, [atualizar a versão do Adobe Commerce na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X para a versão de patch mais recente 2.4.X-pY.
* Se um arquivo/hotfix de patch físico não estiver disponível, [atualizar a versão do Adobe Commerce no local](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X para a versão de patch mais recente 2.4.X-pY.

## Leitura relacionada

* Consulte [Notas de versão do Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) no *Guia da infraestrutura do Adobe Commerce na nuvem*.
* Consulte [Atualizar a versão do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) no *Guia da infraestrutura do Adobe Commerce na nuvem*.
