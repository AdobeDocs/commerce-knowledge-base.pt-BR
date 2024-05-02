---
title: "MDVA-12304: erro 503 no store front e erro de cookie"
description: Esse patch do MDVA-12304 Adobe Commerce resolve 503 erros nas frentes da loja, com *Não é possível enviar o cookie. O número máximo de cookies seria excedido.* mensagem de erro nos logs. Este é um problema conhecido do Adobe Commerce 2.2.5. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: erro 503 na frente da loja e erro de cookie

Esse patch do MDVA-12304 Adobe Commerce resolve 503 erros nas frentes da loja, com *Não foi possível enviar o cookie. O número máximo de cookies seria excedido.* mensagem de erro nos logs. Este é um problema conhecido do Adobe Commerce 2.2.5. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.12 está instalado.

## Produtos e versões afetados

* **O patch é criado para a versão do Adobe Commerce:** Adobe Commerce no local 2.2.5.
* **Compatível com as versões do Adobe Commerce:** Adobe Commerce (todos os métodos de implantação) 2.x.x.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes recebem um erro 503 ao navegar pela loja. No `var/log/exception.log` arquivo, há a seguinte mensagem de erro *Não foi possível enviar o cookie. O número máximo de cookies seria excedido.*

O problema ocorre porque o limite de cookies padrão do Adobe Commerce está definido como 50 e, se o navegador do cliente atingir o limite, o Commerce acionará uma exceção. A solução fornecida no patch aumenta o limite de cookies para 200.

<u>Etapas a serem reproduzidas:</u>

O erro 503 pode ser exibido a qualquer momento quando o cliente está tentando fazer logon e ver o carrinho.

No `var/log/exception.log` arquivo, há a seguinte mensagem de erro *Não foi possível enviar o cookie. O número máximo de cookies seria excedido.*

<u>Resultado real:</u> O cliente não consegue verificar o carrinho ou concluir o pedido.

<u>Resultado esperado:</u> O cliente pode verificar o carrinho e concluir o pedido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.


## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
