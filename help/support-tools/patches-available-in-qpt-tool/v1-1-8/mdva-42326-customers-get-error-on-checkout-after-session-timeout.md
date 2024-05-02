---
title: "MDVA-42326: os clientes recebem um erro no check-out após o tempo limite da sessão"
description: O patch MDVA-42326 resolve o problema em que os clientes recebem um erro no check-out após o tempo limite da sessão, mesmo se o Carrinho de compras persistente estiver ativado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalada. A ID do patch é MDVA-42326. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Os clientes recebem um erro no check-out após o tempo limite da sessão

O patch MDVA-42326 resolve o problema em que os clientes recebem um erro no check-out após o tempo limite da sessão, mesmo se o Carrinho de compras persistente estiver ativado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.8 está instalado. A ID do patch é MDVA-42326. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes recebem um erro no check-out após o tempo limite da sessão, mesmo se o carrinho de compras persistente estiver ativado.

<u>Pré-requisitos</u>:

1. Ir para **Configuração** > **Geral** > **Web** > **Configurações de cookie padrão** > **Duração do cookie** e definida como **120**.
1. Ir para **Configuração** > **Clientes** > **Configuração do cliente** > **Opções de clientes on-line** e defina ambos os valores como **2**.
1. Ir para **Configuração** > **Clientes** > **Carrinho de compras persistente** e definida como **Ativar**.
1. Ir para **Configuração** > **Vendas** > **Métodos de pagamento** e desativar todos os métodos de pagamento, exceto **Cheque/Ordem de pagamento** (deve ser ativado).

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como cliente e adicione alguns produtos ao carrinho.
1. Verifique o carrinho de compras.
1. Aguarde dois minutos (definido na pré-condição); a sessão deve expirar.
1. Clique em **Ir para check-out** e não atualizam a página.
1. Faça check-out como convidado, preencha o endereço de envio e escolha um método de envio.
1. Clique em **Próxima**.
1. No **Revisão e Pagamentos** clique em **Fazer pedido**. Uma vez que apenas um método de pagamento é permitido, o cliente deve ser capaz de colocar a ordem sem selecionar o método de pagamento.

<u>Resultados esperados</u>:

O cliente deve poder fazer o pedido.

<u>Resultados reais</u>:

O cliente recebe o seguinte erro: *Falha na validação do endereço: o email tem um formato incorreto*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
