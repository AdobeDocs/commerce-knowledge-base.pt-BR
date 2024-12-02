---
title: 'MDVA-38827: Os clientes recebem o erro de envio de pedido por email'
description: 'O patch MDVA-38827 corrige o problema em que os clientes recebem um email de envio de pedido contendo a seguinte mensagem de erro: *Desculpe, ocorreu um erro ao gerar esse conteúdo*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 está instalada. A ID do patch é MDVA-38827. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.'
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Os clientes recebem o erro de envio de pedido por email

O patch MDVA-38827 corrige o problema em que os clientes recebem um email de remessa de pedido contendo a seguinte mensagem de erro: *Ocorreu um erro ao gerar este conteúdo*. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 está instalada. A ID do patch é MDVA-38827. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando a opção Notificar Clientes por Email para remessa está selecionada, os clientes recebem um email contendo a seguinte mensagem de erro: *Ocorreu um erro ao gerar este conteúdo*.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Marketing** > **Comunicações** > **Modelos de email** e selecione **Adicionar Novo Modelo**.
   * Selecione **Vendas de Magento** > **Nova Remessa**.
   * Clique em **Carregar Modelo**.
   * Adicione um nome de modelo (por exemplo, Modelo de envio principal) e clique em **Salvar**.
1. Ir para **Loja** > Configurações > **Configuração** > **Vendas** > **Email de Vendas**:
   * Habilitar **Comentários da Remessa**.
   * Selecione **Modelo de envio principal** (consulte a parte &quot;Adicionar um nome de modelo&quot; da Etapa 1) em Modelo de email de comentário de remessa e Modelo de email de comentário de remessa para convidado.
1. Fazer um pedido. Vá para o painel Administrador > **Vendas** > **Pedido**, clique em **Exibir** e envie o pedido.
1. O estado do pedido será alterado de Pendente para Processando.
1. Clique em **Remessas** no menu da barra lateral esquerda e em **Exibir** para ver o pedido.
1. Adicione um comentário ao **Texto do Comentário** abaixo de **Histórico da Remessa** e marque a caixa de seleção **Notificar Cliente por Email**.
1. Clique em **Enviar Comentário**.

<u>Resultados esperados</u>:

Email de vendas com comentários de remessa gerado.

<u>Resultados reais</u>:

A seguinte mensagem de erro é recebida no email: *Ocorreu um erro ao gerar este conteúdo.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
