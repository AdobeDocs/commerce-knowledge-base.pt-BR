---
title: "MDVA-28191: Nenhum método de pagamento para um site no Administrador Cria um Novo Pedido"
description: O patch MDVA-28191 corrige o problema em que um método de pagamento não está carregando no Admin **Criar novo pedido** para um site, embora os métodos de pagamento possam ser exibidos para outros sites.  Este patch está disponível quando a ferramenta [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versão 1.0.5 está instalada.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: Nenhum método de pagamento para um site no Administrador Cria Novo Pedido

O patch MDVA-28191 corrige o problema em que um método de pagamento não está carregando no Admin **Criar novo pedido** para um site, embora os métodos de pagamento possam ser exibidos para outros sites.  Este patch está disponível quando a ferramenta [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versão 1.0.5 está instalada.

## Produtos e versões afetados

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.3 a 2.4.1 (incluindo 2.3.5-p1).

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao criar um pedido no back-end, o Adobe Commerce cria duas cotas, uma está inativa e a outra está ativa. Mas a sessão contém a ID de cotação inativa.

<u>Etapas a serem reproduzidas</u>

1. Vá para **Painel de administração** > **Vendas** > **Pedidos** e clique no botão **Criar novo pedido**.
1. Escolha o cliente para o qual deseja criar a ordem.
1. Se o armazenamento tiver vários modos de exibição, escolha o modo de exibição de armazenamento no qual o pedido deve ser feito, na página **Criar novo pedido** para o usuário selecionado.
1. Adicione produtos da seção **Atividades do cliente** ou do catálogo clicando em **Adicionar produtos**. Role a página para baixo para concluir as seguintes seções, conforme necessário para o pedido:
   * Aplicar Códigos De Cupom
   * Método de pagamento
   * Método de envio
   * Comentários do pedido

<u>Resultado esperado:</u>

Os métodos de pagamento devem ser carregados no Administrador para todos os sites.

<u>Resultado real:</u>

Nenhum método de pagamento disponível (a mensagem &quot;*Nenhuma Informação de Pagamento Necessária*&quot; também não é exibida) para este site, embora os métodos de pagamento possam ser exibidos ao testar pedidos de outros sites.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
