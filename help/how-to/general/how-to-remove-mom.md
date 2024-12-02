---
title: Como remover o Magento Order Management (MOM)
description: Este artigo explica como remover o sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Como remover o Magento Order Management (MOM)

1. Desabilite a integração do MOM seguindo as etapas em [Desabilitar ou habilitar a integração](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Desabilite o módulo MOM seguindo as etapas em [Desinstalar módulos](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Para extrair dados completos do pedido, oferecemos a API. Você pode saber mais revisando o [Repositório de Pedidos](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) em nosso Adobe | Documentação do Magento OMS, que abrangem informações de pedidos (order_repository). Use a [seção de especificações](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) em nosso Adobe | Documentação do Magento OMS para usar outras APIs para extrair tipos de informações diferentes.
