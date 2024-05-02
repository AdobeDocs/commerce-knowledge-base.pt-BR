---
title: Atualização para o esquema DHL v10 para continuar oferecendo envio para DHL
description: Este artigo fornece uma solução para permitir que os comerciantes continuem oferecendo o envio da DHL após a desativação do esquema DHL 6.2 em dezembro de 2022, atualizando para o esquema 10.0 ou aplicando o patch AC-3023.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Atualize para o esquema DHL versão 10.0 para continuar oferecendo o envio para a DHL

Este artigo fornece uma solução para permitir que os comerciantes continuem oferecendo o transporte para a DHL depois que a versão 6.2 do esquema da DHL for descontinuada no final de dezembro de 2022.

## Produtos e versões afetados

* Adobe Commerce 2.4.5 e versões anteriores, todos os métodos de implantação.

## Problema

Em agosto de 2022, lançamos o [atualização do esquema DHL versão 6.2. juntamente com uma correção](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) para que os comerciantes continuassem a oferecer serviços de transporte à DHL. A DHL está introduzindo novamente um esquema mais recente, a versão 10.0, em outubro de 2022, e a versão anterior (esquema 6.2) será descontinuada no final de dezembro de 2022. O Adobe Commerce 2.4.5 e a integração anterior da DHL são compatíveis apenas com a versão 6.2.

## Solução

O Adobe Commerce 2.4.5-p1 e 2.4.4-p2, lançados em outubro de 2022, contêm o novo esquema DHL versão 10.0. Portanto, os comerciantes que atualizam para 2.4.5-p1 e 2.4.4-p2 não precisam fazer nada para continuar oferecendo os carregamentos da DHL. Recomendamos que todos os comerciantes atualizem para 2.4.5-p1 e 2.4.4-p2 antes da desativação do esquema DHL 6.2 no final de dezembro de 2022.

Os comerciantes que não desejam atualizar para 2.4.5-p1 e 2.4.4-p2 precisarão aplicar um patch fixo se quiserem continuar oferecendo o envio para a DHL após dezembro de 2022.

## Correção

O ID do patch é AC-3023 e está disponível no [!DNL Quality Patches Tool] versão 1.1.21.

Consulte os links a seguir para saber como usar o [!DNL Quality Patches Tool] e instale patches dependendo de seus métodos de implantação:

* Adobe Commerce no local e Magento Open Source: [Ferramentas de correção de qualidade > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no Adobe Experience League.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

**O patch é aplicável às seguintes versões do Adobe Commerce (todos os métodos de implantação):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Links úteis

* [[!DNL Quality Patches Tool] > Notas de versão](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) no Adobe Experience League.

* [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no Adobe Experience League.

## Leitura relacionada

* [Aplique um patch para continuar oferecendo a DHL como transportadora](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) em nossa base de conhecimento de suporte.

* [Transportadoras > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) em nosso guia do usuário.
* [Referência de Configuração > Vendas > Métodos de Distribuição](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) em nosso guia do usuário.
