---
title: "ACSD-43887: detalhes incorretos exibidos na página de pagamento do check-out"
description: O patch ACSD-43887 corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando os Pedidos de compra para empresas estão ativados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-43887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887: detalhes incorretos exibidos na página de pagamento do check-out

O patch ACSD-43887 corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando os Pedidos de compra para empresas estão ativados. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.17 está instalado. A ID do patch é ACSD-43887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Detalhes incorretos são exibidos na página de pagamento de check-out quando Ordens de compra para empresas estão habilitadas.

<u>Pré-requisitos</u>:

1. Os módulos B2B são instalados.
1. Ativar empresa está definido como _Sim_. Ir para **Lojas** > **Configurações** > **Geral** > **Recursos B2B** > **Ativar empresa** > **Sim**.
1. Ativar Ordens de Compra está definido como _Sim_. Ir para **Configuração de aprovação de pedido** > **Habilitar Ordens de Compra** > **Sim**.
1. O PayPal Express está configurado como o método de pagamento.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto virtual.
1. Registre uma conta da empresa do front-end com um Administrador de empresa.
1. Aprove a conta da empresa do back-end e defina **Habilitar Ordens de Compra** as _Sim_ ao aprovar a empresa.
1. Acesse o front-end e faça logon usando a conta de administrador da empresa criada na etapa dois.
1. Crie um &quot;Usuário padrão&quot; para a empresa. Ir para **Usuário da empresa** > **Adicionar novo usuário**.
1. Crie uma &quot;Regra de aprovação&quot; para a empresa. Ir para **Regras de aprovação** > **Adicionar nova regra**.

   * Tipo de regra: Total da ordem
   * Total do pedido: é maior que ou igual a US$ 1
   * Exige aprovação de: Administrador da empresa

1. Faça logout e login usando a conta &quot;Usuário padrão&quot;.
1. Adicione o produto virtual criado na etapa um ao carrinho e prossiga para o check-out.
1. Selecione PayPal Express como o método de pagamento e clique em **Fazer Ordem de Compra**.
1. Faça logoff e logon usando a conta de administrador da empresa.
1. Ir para **Minhas Ordens de Compra** e de **Ordens de Compra da Empresa**, clique em **Exibir** para o pedido criado na etapa nove.
1. Aprovar a ordem de compra. O status da ordem de compra deve ser &quot;Aprovado: Pagamento Pendente&quot;.
1. Faça logout e login usando a conta &quot;Usuário padrão&quot; da empresa.
1. Ir para **Minhas Ordens de Compra** > **Exibir** > **Fazer pedido**.
1. Verifique a **Resumo do pedido**.

<u>Resultados esperados</u>:

O resumo do pedido mostra valores diferentes de zero corretos.

<u>Resultados reais</u>:

O valor total do resumo do pedido é zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
