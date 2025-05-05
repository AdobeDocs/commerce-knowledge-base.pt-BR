---
title: Resolução de erros UTF-8 para uploads de arquivo CSV
description: Este artigo fornece uma correção para quando você recebe a mensagem de erro "Os arquivos CSV devem usar a codificação UTF-8". Esta mensagem de erro significa que o arquivo que você está tentando carregar contém caracteres ilegais ou não permitidos. Embora a codificação UTF-8 permita [a maioria dos caracteres](https://www.fileformat.info/info/charset/UTF-8/list.htm), alguns não são compatíveis com o Magento BI.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Resolução de erros UTF-8 para uploads de arquivo CSV

Este artigo fornece uma correção para quando você recebe a mensagem de erro &quot;Os arquivos CSV devem usar a codificação UTF-8&quot;. Esta mensagem de erro significa que o arquivo que você está tentando carregar contém caracteres ilegais ou não permitidos. Embora a codificação UTF-8 permita [a maioria dos caracteres](https://www.fileformat.info/info/charset/UTF-8/list.htm), alguns não são compatíveis com o Magento BI.

Para corrigir o problema, será necessário alterar a codificação do arquivo. Salvar novamente o arquivo com a codificação adequada normalmente resolve o problema, mas esteja ciente de que você pode perder algumas informações (por exemplo, os caracteres ilegais podem ser descartados) ao fazer isso.

Recomendamos usar [Texto Sublime](https://www.sublimetext.com/2) para salvar e codificar o arquivo.

1. Abra o arquivo no Microsoft Excel, Google Docs, Apple Numbers ou no programa de sua escolha.
1. Clique em &#x200B;&#x200B; **Arquivo** > **Salvar como** &#x200B; &#x200B; &#x200B; &#x200B;e escolha o formato separados por vírgula **Var.** para salvar o arquivo.
1. Abra o arquivo CSV em Texto sublime.
1. Em Texto Sublime, navegue até &#x200B;&#x200B; **Arquivo** > **Salvar com Codificação** > **UTF-8\*&#x200B;** . Isso salvará o arquivo CSV com codificação UTF-8.    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [Carregar os dados](https://experienceleague.adobe.com/pt-br/docs/commerce-business-intelligence/mbi/analyze/connecting/using-file-uploader) (em nosso guia do usuário) para uma nova tabela no Magento BI.
