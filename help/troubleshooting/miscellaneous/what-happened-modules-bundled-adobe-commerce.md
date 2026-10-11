---
title: Módulos ausentes do Adobe Commerce 2.4.4
description: Este artigo fornece uma solução para o problema quando os módulos incluídos nas versões anteriores do Adobe Commerce não estão presentes na versão 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# Módulos ausentes do Adobe Commerce 2.4.4

Este artigo fornece uma solução para quando os módulos incluídos nas versões anteriores do Adobe Commerce não estiverem presentes na versão 2.4.4.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Não é possível instalar um módulo de terceiros ou você descobriu que algumas das principais extensões agrupadas não estão presentes quando você atualizou para o Adobe Commerce 2.4.4. Isso só deve ser resultado da instalação de um módulo de terceiros que exija uma das extensões agrupadas removidas do Adobe Commerce 2.4.4 ou se o projeto utilizar alguma da funcionalidade de um dos módulos removidos.

* Cenário 1: o projeto utilizou uma das funcionalidades principais do módulo empacotado. O módulo empacotado utilizado não está incluído no Adobe Commerce 2.4.4. Depois de atualizar com êxito para o Adobe Commerce 2.4.4, você percebe que o módulo e sua funcionalidade fornecida estão ausentes.

* Cenário 2: você tem um módulo instalado no projeto atual que tem uma dependência em um dos módulos agrupados removidos.

Esse comportamento é esperado, pois as extensões agrupadas por fornecedores foram removidas da base de código do Adobe Commerce 2.4.4.

## Solução

Instale/compre as extensões oficiais separadamente. Eles estão disponíveis na [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Leitura relacionada

[Vendor-Bundled Extensions](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?lang=pt-BR&#vendor-bundled-extensions) em Adobe Commerce Documentation > Informações da versão > Notas de versão do Adobe Commerce 2.4.4.
