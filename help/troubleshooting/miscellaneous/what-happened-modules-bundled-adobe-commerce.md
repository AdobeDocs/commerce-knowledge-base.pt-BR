---
title: Módulos ausentes do Adobe Commerce 2.4.4
description: Este artigo fornece uma solução para o problema quando os módulos incluídos nas versões anteriores do Adobe Commerce não estão presentes na versão 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Módulos ausentes do Adobe Commerce 2.4.4

Este artigo fornece uma solução para quando os módulos incluídos nas versões anteriores do Adobe Commerce não estiverem presentes na versão 2.4.4.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) all  [versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Não é possível instalar um módulo de terceiros ou você descobriu que algumas das principais extensões agrupadas não estão presentes quando você atualizou para o Adobe Commerce 2.4.4. Isso só deve ser resultado da instalação de um módulo de terceiros que exija uma das extensões agrupadas removidas do Adobe Commerce 2.4.4 ou se o projeto utilizar alguma da funcionalidade de um dos módulos removidos.

* Cenário 1: o projeto utilizou uma das funcionalidades principais do módulo empacotado. O módulo empacotado utilizado não está incluído no Adobe Commerce 2.4.4. Depois de atualizar com êxito para o Adobe Commerce 2.4.4, você percebe que o módulo e sua funcionalidade fornecida estão ausentes.

* Cenário 2: você tem um módulo instalado no projeto atual que tem uma dependência em um dos módulos agrupados removidos.

Esse comportamento é esperado, pois as extensões agrupadas por fornecedores foram removidas da base de código do Adobe Commerce 2.4.4.

## Solução

Instale/compre as extensões oficiais separadamente. Eles estão disponíveis no [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Leitura relacionada

[Extensões agrupadas pelo fornecedor](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) em Adobe Commerce Documentation > Release Information > Adobe Commerce 2.4.4 release notes.
