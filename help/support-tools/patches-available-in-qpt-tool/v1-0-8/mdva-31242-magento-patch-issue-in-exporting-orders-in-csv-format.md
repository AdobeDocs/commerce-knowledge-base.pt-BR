---
title: "MDVA-31242: problema ao exportar pedidos no formato CSV"
description: O patch MDVA-31242 resolve o problema em que ocorre um erro ao exportar pedidos no formato de arquivo CSV. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 1e343f23-5b10-492b-885f-8113ace4777f
feature: B2B, Data Import/Export, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-31242: problema na exportação de pedidos no formato CSV

O patch MDVA-31242 resolve o problema em que ocorre um erro ao exportar pedidos no formato de arquivo CSV. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (métodos de implantação) 2.3.0 - 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no back-end do Administrador.
1. Habilitar **Empresa** em **Lojas** > **Configuração** > **Recursos B2B**.
1. Vá para **Vendas** > **Pedidos**.
1. Clique na caixa de seleção **Coluna** > **Nome da Empresa**.
1. Insira qualquer valor no campo de texto **Filtros** > **Nome da Empresa**.
1. Clique no botão **Aplicar Filtros**.
1. Clique no botão **Export** > **CSV** > **Export**.

<u>Resultados esperados</u>:

O pop-up de arquivo selecionado é aberto conforme esperado.

<u>Resultados reais</u>:

Uma tela branca com o erro *Houve um erro ao processar sua solicitação*. A exceção é exibida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
