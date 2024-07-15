---
title: "MDVA-39163: Métodos de envio não disponíveis para usuários recém-registrados com produtos da sessão de convidado"
description: O patch MDVA-39163 resolve o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-39163. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: Métodos de envio não disponíveis para usuários recém-registrados com produtos da sessão de convidado

O patch MDVA-39163 resolve o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-39163. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os métodos de envio não estão disponíveis quando o novo usuário é registrado e os produtos no carrinho são da sessão de convidado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Admin** > **Lojas** > **Configuração** > **Vendas** > **Métodos de Entrega**. Habilite somente o método de envio **Taxa Uniforme** e desabilite todo o resto.
1. No método de envio **Taxa Uniforme**, selecione a opção de país **Específico** disponível na configuração **Remeter para Países Aplicáveis** e selecione um país da lista (por exemplo, Estados Unidos).
1. Acesse **Administrador** > **Lojas** > **Configuração** > **Cliente** > **Configuração do Cliente** e defina **Exigir Confirmação de Email** para _Sim_.
1. Crie um novo Modelo de email em **Admin** > **Marketing** > **Modelos de email** e carregue o modelo `Footer (magento/luma)` e substitua o conteúdo do modelo por um bloco CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Vá para **Admin** > **Conteúdo** > **Design** > **Configuração** e selecione o tema relacionado ao site de front-end. Defina o &quot;Modelo de rodapé&quot; para o novo modelo de email criado.
1. Acesse o front-end e adicione um produto ao carrinho.
1. Crie um cliente; você receberá um email para confirmar o endereço de email. Clique no link de verificação. Você será conectado ao site.
1. Vá para **Minha conta** e adicione um endereço. Defina o país do endereço para o país de entrega definido na configuração do administrador anteriormente.
1. Vá para o check-out.

<u>Resultados esperados</u>:

O método de envio está disponível, pois o cliente tem um endereço compatível com o país de envio.

<u>Resultados reais</u>:

Método de envio não disponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
