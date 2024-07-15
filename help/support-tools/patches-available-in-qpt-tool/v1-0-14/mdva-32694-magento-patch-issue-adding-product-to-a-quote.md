---
title: "Patch MDVA-32694: problema ao adicionar produto a uma cotação"
description: O patch MDVA-32694 resolve o problema de não ser possível adicionar um produto válido no Admin a uma cotação negociável criada no site fora do padrão.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Correção MDVA-32694: problema ao adicionar produto a uma cotação

O patch MDVA-32694 resolve o problema de não ser possível adicionar um produto válido no Admin a uma cotação negociável criada no site fora do padrão.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.2 com B2B versão 1.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisitos</u>:

Instale uma nova instância do Adobe Commerce com B2B.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **LOJAS > Configuração > GERAL > Recursos B2B** e habilite a **Empresa** e a **Cotação B2B**.
1. Crie mais 2 sites com **lojas** e **storeview** (No total, você deve ter 3 sites: *base*, *site2*, *site3*).
1. Crie um produto simples e atribua-o somente ao *site3*.
1. Vá para **LOJAS > Todas as lojas** e defina o *site3* como **padrão**.
1. Vá para o front-end e crie uma nova empresa no *site3*.
1. Adicione o produto criado anteriormente ao carrinho e crie uma nova cotação negociável.
1. Vá para **LOJAS > Todas as lojas** e defina o site &quot;*base*&quot; novamente como **padrão**.
1. Acesse **VENDAS > Cotações > Abrir cotação criada anteriormente** e tente adicionar o mesmo produto a ela.

<u>Resultados esperados</u>:

O usuário Administrador pode adicionar o mesmo produto à cotação, conforme esperado.

<u>Resultados reais</u>:

O usuário administrador não pode adicionar o mesmo produto à cotação e esta mensagem de erro é exibida:

```php
This product is assigned to another website.
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
