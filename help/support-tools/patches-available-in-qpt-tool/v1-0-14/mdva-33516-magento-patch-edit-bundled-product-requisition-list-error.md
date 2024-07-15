---
title: "Patch MDVA-33516: editar erro de Lista de solicitações de produto agrupado"
description: O patch MDVA-33516 corrige o problema em que, ao editar o tipo de produto de pacote a partir da Lista de Requisições, você é redirecionado para uma página de erro de item de lista de requisições. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 76a16982-f977-4674-b05e-23f4ac355d52
feature: B2B, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Correção do MDVA-33516: erro de edição da Lista de solicitações do produto agrupado

O patch MDVA-33516 corrige o problema em que, ao editar o tipo de produto de pacote a partir da Lista de Requisições, você é redirecionado para uma página de erro de item de lista de requisições. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro ao editar produtos agrupados na Lista de Requisições.

<u>Pré-requisitos</u>:

* B2B está instalado.
* A Lista de Requisições está habilitada.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto empacotado com dois produtos simples.
1. Vá para a página do produto agrupado e clique no botão **Personalizar e Adicionar ao carrinho**.
1. Selecione uma das opções na lista suspensa, clique em **Adicionar à Lista de Requisições** para criar uma nova lista de requisições. Para obter etapas detalhadas, consulte [Guia do Usuário do Magento > Minhas Listas de Requisições > Criar uma lista de requisições](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html#create-a-requisition-list) em nosso guia do usuário.
1. Vá para a Lista de Requisições recém-criada (Minha Conta > **Minhas Listas de Requisições**).
1. Clique no botão **Exibir** na coluna *Ações*.
1. Clique no botão **Editar**.

<u>Resultados Esperados</u>:<br>

Nenhum erro.

<u>Resultados Reais</u>:

A página &quot;Sua personalização&quot;, que contém uma imagem do produto incluído, o preço e a seguinte mensagem de erro:

```
Fatal error: Uncaught Error: Call to a member function isAvailableForCompare() on null in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml:1 Stack trace: #0 /var/www/html/vendor/magento/framework/View/TemplateEngine/Php.php(59): include() #1 /var/www/html/vendor/magento/framework/View/Element/Template.php(271): Magento\Framework\View\TemplateEngine\Php->render(Object(Magento\Catalog\Block\Product\View\AddTo\Compare), '/var/www/html/v...', Array) #2 /var/www/html/vendor/magento/framework/View/Element/Template.php(301): Magento\Framework\View\Element\Template->fetchView('/var/www/html/v...') #3 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1099): Magento\Framework\View\Element\Template->_toHtml() #4 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1103): Magento\Framework\View\Element\AbstractBlock->Magento\Framework\View\Element   {closure} () #5 /var/www/html/vendor/magento/framework/View/Element/ in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml
  on line 1
```

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
