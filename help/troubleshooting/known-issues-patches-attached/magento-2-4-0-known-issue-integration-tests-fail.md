---
title: "Problema conhecido do Adobe Commerce 2.4.0: falha nos testes de integração"
description: Este artigo fornece um patch para o problema do Adobe Commerce 2.4.0 em que os testes de integração estão falhando porque a declaração de "Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()" não é compatível com a PHPUnit 9 usada para 2.4.0.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: falha nos testes de integração

Este artigo fornece um patch para o problema do Adobe Commerce 2.4.0 em que os testes de integração estão falhando porque a declaração de `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` não é compatível com a PHPUnit 9 usada para 2.4.0.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Problema

<u>Etapas a serem reproduzidas</u>

Execute testes de integração 2.4.0.

<u>Resultado esperado</u>

Êxito nos testes.

<u>Resultado real</u>

*Erro fatal do PHP: a declaração de Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() deve ser compatível com PHPUnit\\Framework\\TestCase::setUp(): void em /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php na linha 36*

## Solução

Aplique o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte para obter instruções.

## Arquivos Anexados
