---
title: "ACSD-51907: O usuário administrador restrito não pode criar aviso de crédito para reembolso offline"
description: Aplique o patch ACSD-51907 para corrigir o problema do Adobe Commerce em que o usuário administrador restrito não pode criar um aviso de crédito com um reembolso offline.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: O usuário administrador restrito não pode criar aviso de crédito para reembolso offline

O patch ACSD-51907 corrige o problema de desempenho em que o usuário administrador restrito não pode criar um memorando de crédito com um reembolso offline. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.33 está instalado. A ID do patch é ACSD-51907. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador restrito não pode criar um aviso de crédito com um reembolso offline.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **cliente** no site padrão.
1. Criar **novo site** com relacionados *loja* e *exibição de loja*.
1. Defina o site padrão para o novo site, limpe os caches.
1. Alterar configuração do cliente: **Admin** > **Loja** > **Configuração** > **Clientes** > **Configuração do cliente** > **Compartilhar contas de clientes = Global**.
1. Crie uma nova função de usuário administrador com o escopo da função definido para o novo site criado *(acesso somente aos dados de vendas)* in **Admin** > **Sistema** > **Permissões**.
1. Crie uma nova conta de administrador com esta função.
1. Criar novo pedido usando a forma de pagamento online *(por exemplo, Auth.net ou PayPal)*.
1. Faça logon como um usuário administrador restrito.
1. Ir para **Vendas** > **Pedidos** > depois **página de exibição do pedido**.
1. Criar uma NFF.
1. Navegue até a guia NFFs.
1. Clique em **Fatura**.
1. Clique em **[!UICONTROL Credit Memo]**.
1. Verifique a **[!UICONTROL Refund to Store Credit]** , defina o campo de texto próximo a ele como *1* valor.
1. Clique no link **[!UICONTROL Refund Offline]** botão.

<u>Resultados esperados</u>:

O memorando de crédito é criado e *$ 1* é reembolsado ao crédito da loja.

<u>Resultados reais</u>:

A mensagem de erro, *São necessárias mais permissões para exibir este item* é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
