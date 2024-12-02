---
title: 'MDVA-42326: Os clientes recebem um erro no check-out após o tempo limite da sessão'
description: O patch MDVA-42326 resolve o problema em que os clientes recebem um erro no check-out após o tempo limite da sessão, mesmo se o Carrinho de compras persistente estiver ativado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalada. A ID do patch é MDVA-42326. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Os clientes recebem um erro no check-out após o tempo limite da sessão

O patch MDVA-42326 resolve o problema em que os clientes recebem um erro no check-out após o tempo limite da sessão, mesmo se o Carrinho de compras persistente estiver ativado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 está instalada. A ID do patch é MDVA-42326. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes recebem um erro no check-out após o tempo limite da sessão, mesmo se o carrinho de compras persistente estiver ativado.

<u>Pré-requisitos</u>:

1. Vá para **Configuração** > **Geral** > **Web** > **Configurações de Cookie Padrão** > **Vida Útil do Cookie** e defina como **120**.
1. Vá para **Configuração** > **Clientes** > **Configuração do Cliente** > **Opções de Clientes Online** e defina os dois valores como **2**.
1. Vá para **Config** > **Customers** > **Carrinho de Compras Persistente** e defina como **Habilitar**.
1. Vá para **Config** > **Vendas** > **Métodos de Pagamento** e desative todos os métodos de pagamento, exceto **Cheque/Ordem de Pagamento** (deve ser habilitado).

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como cliente e adicione alguns produtos ao carrinho.
1. Verifique o carrinho de compras.
1. Aguarde dois minutos (definido na pré-condição); a sessão deve expirar.
1. Clique em **Ir para o check-out** e não atualize a página.
1. Faça check-out como convidado, preencha o endereço de envio e escolha um método de envio.
1. Clique em **Avançar**.
1. Na página **Verificação e pagamentos**, clique em **Fazer pedido**. Uma vez que apenas um método de pagamento é permitido, o cliente deve ser capaz de colocar a ordem sem selecionar o método de pagamento.

<u>Resultados esperados</u>:

O cliente deve poder fazer o pedido.

<u>Resultados reais</u>:

O cliente recebe o seguinte erro: *Falha na validação de endereço: o email tem um formato incorreto*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
