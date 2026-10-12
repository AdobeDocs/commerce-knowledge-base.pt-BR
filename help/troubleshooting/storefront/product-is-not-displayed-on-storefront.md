---
title: O produto não é exibido na loja
description: Este artigo fornece soluções para quando os produtos não são exibidos na loja.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
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



