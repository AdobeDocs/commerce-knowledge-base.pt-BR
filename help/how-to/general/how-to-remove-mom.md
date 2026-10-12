---
title: Como remover o Magento Order Management (MOM)
description: Este artigo explica como remover o sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%
---
# Como remover o Magento Order Management (MOM)

1. Desabilite a integração do MOM seguindo as etapas em [Desabilitar ou habilitar a integração](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Desabilite o módulo MOM seguindo as etapas em [Desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html?lang=pt-BR).
1. Para extrair dados completos do pedido, oferecemos a API. Você pode saber mais revisando o [Repositório de Pedidos](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) em nossa Adobe | Documentação do OMS da Magento, que abrange informações do pedido (order_repository). Use a [seção de especificações](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) em nossa Adobe | Documentação do OMS da Magento para usar outras APIs para extrair tipos de informações diferentes.
