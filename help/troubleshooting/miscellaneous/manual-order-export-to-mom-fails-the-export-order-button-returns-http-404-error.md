---
title: Falha na exportação manual da ordem para o MOM. O botão Exportar pedido retorna o erro HTTP 404
description: Este artigo discute como corrigir um problema, no qual tentar exportar um pedido para o Magento Order Management (MOM) clicando no botão **Exportar pedido** na exibição do pedido no Commerce Admin retorna o erro " *404 Página não encontrada*".
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Falha na exportação manual da ordem para o MOM. O botão Exportar pedido retorna o erro HTTP 404

Este artigo explica como corrigir um problema, no qual tentar exportar um pedido para o Magento Order Management (MOM) clicando no botão **Exportar pedido** na exibição do pedido no Commerce Admin retorna o erro &quot; *404 Página não encontrada* &quot;.

## Produtos e versões afetados

* Adobe Commerce 2.2.x, 2.3.x
* Conector MOM 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problema

<u>Etapas a serem reproduzidas:</u>:

1. No Administrador do Commerce, clique em **Vendas > Pedidos**.
1. Clique no botão **Criar novo pedido**.
1. Selecione um usuário, adicione um ou mais itens, escolha métodos de pagamento e envio e clique no botão **Enviar Pedido**.
1. Clique no botão **Exportar pedido** e em **OK**.

<u>Resultado esperado</u>:

O pedido é enviado ao MOM.

<u>Resultado real</u>:

Uma página &quot; *404 Erro: Página não encontrada* &quot; é exibida.

## Solução

* Atualize o Conector MOM para 3.4.0 para Adobe Commerce 2.3.x ou Conector MOM 2.5 para Adobe Commerce 2.2.x.
* Se o upgrade do conector MOM não for uma opção, você poderá exportar a ordem para o Magento Order Management usando o comando da CLI:

```bash
$bin/magento oms:orders:sync
```

## Leitura relacionada

[documentação técnica do Magento Order Management](https://omsdocs.magento.com/en/)
