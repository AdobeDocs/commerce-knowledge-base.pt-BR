---
title: "MDVA-38827: Os clientes recebem o erro de envio de pedido por email"
description: "O patch MDVA-38827 corrige o problema em que os clientes recebem um email de envio de pedido contendo a seguinte mensagem de erro: *Desculpe, ocorreu um erro ao gerar esse conteúdo*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 está instalada. A ID do patch é MDVA-38827. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Os clientes recebem o erro de envio de pedido por email

O patch MDVA-38827 corrige o problema em que os clientes recebem um email de envio de pedido contendo a seguinte mensagem de erro: *Ocorreu um erro ao gerar este conteúdo*. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.1.0 está instalado. A ID do patch é MDVA-38827. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando a opção Notificar Clientes por Email para entrega é selecionada, os clientes recebem um email contendo a seguinte mensagem de erro: *Ocorreu um erro ao gerar este conteúdo*.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Marketing** > **Comunicações** > **Modelos de e-mail** e selecione **Adicionar novo modelo**.
   * Selecionar **Vendas Magento** > **Nova Remessa**.
   * Clique em **Carregar modelo**.
   * Adicione um nome de modelo (por exemplo, Modelo de envio principal) e clique em **Salvar**.
1. Ir para **Loja** > Configurações > **Configuração** > **Vendas** > **E-mail de vendas**:
   * Ativar **Comentários da Remessa**.
   * Selecionar **Modelo principal de envio** (consulte a parte &quot;Adicionar um nome de modelo&quot; da Etapa 1) em Modelo de email de comentário de remessa e Modelo de email de comentário de remessa para convidado.
1. Fazer um pedido. Ir para o painel Administração > **Vendas** > **Pedido**, clique em **Exibir** e, em seguida, envie o pedido.
1. O estado do pedido será alterado de Pendente para Processando.
1. Clique em **Entregas** no menu da barra lateral esquerda e clique em **Exibir** para ver o pedido.
1. Adicionar um comentário no **Texto do comentário** abaixo **Histórico de Remessa** e marque a caixa de seleção **Notificar Cliente por Email**.
1. Clique em **Enviar comentário**.

<u>Resultados esperados</u>:

Email de vendas com comentários de remessa gerado.

<u>Resultados reais</u>:

A seguinte mensagem de erro é recebida no email: *Ocorreu um erro ao gerar este conteúdo.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
