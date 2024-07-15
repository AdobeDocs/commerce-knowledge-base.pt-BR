---
title: O produto não é exibido na loja
description: Este artigo fornece soluções para quando os produtos não são exibidos na loja.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# O produto não é exibido na loja

Este artigo fornece soluções para quando os produtos não são exibidos na loja.

## Produtos e versões afetados

* Adobe Commerce no local X.X.X
* Adobe Commerce na infraestrutura em nuvem X.X.X

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce.
1. Ir para **Catálogo** > **Produtos**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Clique em **Adicionar produto** e passe pelo processo de criação do produto. Ou importe produtos de um arquivo CSV.

<u>Resultado esperado</u>:

O produto é exibido na loja.

<u>Resultado real</u>:

O produto não é exibido.

## Causa

Isso pode ser causado por vários motivos. Siga as etapas abaixo para verificar os pontos principais que podem ajudar a identificar e resolver o problema.

## Solução

Cada um dos pontos a seguir pode resolver o problema.

* Verifique as configurações do produto no Admin. Vá para **Catálogo** > **Produtos**, abra a página do produto e verifique se os seguintes campos estão configurados corretamente:
   * **Habilitar Produto** = *Sim.*
   * **Status do Estoque**: *No Estoque*. Ou se *Produto esgotado* for o valor correto, verifique se **Exibir Produtos esgotados** (**LOJAS** > **Configurações** > **Configuração** > **CATÁLOGO** > **Inventário** > **Opções de Estoque** > **Exibir Produtos Não Estocados**) está definido como *Sim* (configurado em nível global).
   * **Categorias**: se você tentar encontrar o produto em uma página de categoria, verifique se o produto está atribuído à categoria. Para simplificar a solução de problemas, crie uma nova categoria da página atual e atribua um produto a ela.
   * **Visibilidade** = *Catálogo, Pesquisa.*
   * Na seção **Produto nos Sites**, verifique se o produto foi atribuído ao site correto.
   * Alterne o seletor de escopo para a visualização da loja onde você tenta encontrar o produto na loja e verifique as mesmas configurações.
* Execute a reindexação completa executando o `bin/magento indexer:reindex` no console e limpe todo o cache no Administrador em **Sistema** > **Ferramentas** > **Gerenciamento de Cache**, ou no console executando o `bin/magento cache:clean`.
* Se isso não ajudar, inicie uma investigação mais detalhada verificando os logs no diretório `var/log`.

## Leitura relacionada em nossa base de conhecimento de suporte

* [Locais de registro (diretórios) para arquitetura Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Locais de log (diretórios) para a arquitetura de Início](/help/how-to/general/log-locations-directories-for-starter-plan.md)
