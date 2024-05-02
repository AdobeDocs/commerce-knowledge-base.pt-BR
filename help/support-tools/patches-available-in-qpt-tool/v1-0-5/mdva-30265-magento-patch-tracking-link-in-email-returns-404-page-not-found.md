---
title: "MDVA-30265: link de rastreamento em retornos de email 404 Página não encontrada"
description: O patch MDVA-30265 resolve o problema do erro "Página 404 não encontrada" quando o cliente clica no link de rastreamento da remessa no email de confirmação do pedido. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: link de rastreamento em retornos de email 404 Página não encontrada

O patch MDVA-30265 resolve o problema do erro &quot;Página 404 não encontrada&quot; quando o cliente clica no link de rastreamento da remessa no email de confirmação do pedido. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.5 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 para 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Depois que a remessa é criada para um pedido feito, um email é enviado ao cliente com informações de rastreamento e um link para rastrear o pedido. No entanto, quando o cliente clica no link de rastreamento de envio no email, isso retorna o erro &quot;Página 404 não encontrada&quot;.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce 2.4. Para obter etapas, consulte [Instalar o Adobe Commerce usando o Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) na documentação do desenvolvedor.
1. Fazer um pedido.
1. Ir para o painel Administração > **Vendas** > **Pedidos**. Procure a ordem que você acabou de criar e abra-a.
1. Crie uma remessa e adicione um número de rastreamento (Transportadora = Valor Personalizado). Para obter etapas, consulte [Order Management > Criando uma Entrega](https://docs.magento.com/user-guide/sales/shipments-create.html) em nosso guia do usuário.
1. Você receberá um email. Clique no link de rastreamento para verificar se ele está funcionando.
1. Criar uma fatura. Para obter etapas, consulte [Order Management > Criando uma NFF](https://docs.magento.com/user-guide/sales/invoice-create.html) em nosso guia do usuário. Em seguida, clique novamente no link de rastreamento acima.

<u>Resultados esperados</u>:

O link de rastreamento deve funcionar mesmo após a criação da fatura.

<u>Resultados reais</u>:

Depois de criar a fatura, o link de rastreamento não funciona e retorna uma página de erro &quot;Página 404 não encontrada&quot;.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
