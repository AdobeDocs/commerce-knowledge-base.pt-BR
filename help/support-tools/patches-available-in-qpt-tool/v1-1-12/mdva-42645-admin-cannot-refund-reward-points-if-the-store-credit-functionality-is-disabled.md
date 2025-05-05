---
title: 'MDVA-42645: O administrador não pode reembolsar pontos de recompensa por crédito de loja desabilitada'
description: O patch MDVA-42645 resolve o problema em que o administrador não pode reembolsar pontos de premiação se a funcionalidade de crédito da loja estiver desativada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42645. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: O administrador não pode reembolsar pontos de recompensa por crédito de loja desabilitada

O patch MDVA-42645 resolve o problema em que o administrador não pode reembolsar pontos de premiação se a funcionalidade de crédito da loja estiver desativada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42645. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Administrador não poderá reembolsar pontos de premiação se a funcionalidade de crédito da loja estiver desabilitada.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Crie uma nova conta de cliente e adicione alguns pontos de premiação.
1. Desabilite a Funcionalidade de Crédito da Loja indo até **Loja** > Configurações > **Configuração** > **Cliente** > **Configuração do Cliente** > **Opções de Crédito da Loja**.
1. Faça logon como o cliente para o qual os pontos de premiação são atribuídos.
1. Adicione um produto ao carrinho e navegue até o check-out.
1. Use os pontos de premiação na seção de pagamento e faça o pedido.
1. Abra o pedido no administrador e fatura o pedido.
1. Clique no link **Memorando de Crédito** para criar um novo memorando de crédito.
1. Marque a opção Reembolsar pontos de recompensa na parte inferior e clique em **Reembolsar offline**.

<u>Resultados esperados</u>:

* O Aviso de Crédito foi criado com sucesso.
* Os pontos de recompensa são reembolsados com sucesso.

<u>Resultados reais</u>:

Você recebe a seguinte mensagem de erro: *Não é possível usar mais crédito de loja do que o valor do pedido.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) na documentação do desenvolvedor.
