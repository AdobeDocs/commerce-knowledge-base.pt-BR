---
title: Remover tentativas de logon com falha do banco de dados
description: Este artigo explica como remover credenciais de logon com falha pré-existentes do banco de dados do Adobe Commerce no local e do Adobe Commerce na infraestrutura em nuvem. Para as versões 2.2.10+ e 2.3.3+, é necessário apenas executar o script anexado. Para versões mais antigas 2.3.0-2.3.2-p2, é necessário aplicar um patch para interromper o registro e executar o script anexado para remover as credenciais de logon com falha pré-existentes.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Remover tentativas de logon com falha do banco de dados

>[!NOTE]
>
>Este artigo foi atualizado em 13 de abril de 2020, com um novo script chamado DB\_CLEANUP\_SCRIPT\_v2. Use o script DB\_CLEANUP\_SCRIPT\_v2 anexado para limpar dados de logon com falha pré-existentes em tabelas adicionais. Você precisa usar DB\_CLEANUP\_SCRIPT\_v2, mesmo que tenha executado DB\_CLEANUP\_SCRIPT\_v1 anteriormente para ajudar a garantir que tabelas adicionais sejam limpas.

Este artigo explica como remover credenciais de logon com falha pré-existentes do banco de dados do Adobe Commerce no local e do Adobe Commerce na infraestrutura em nuvem. Para as versões 2.2.10+ e 2.3.3+, é necessário apenas executar o script anexado. Para versões mais antigas 2.3.0-2.3.2-p2, é necessário aplicar um patch para interromper o registro e executar o script anexado para remover as credenciais de logon com falha pré-existentes.

## **Produtos e versões afetados**

* Esse problema afeta o Magento Open Source, o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x e versões anteriores.
* As implantações do Adobe Commerce 1.x não são afetadas.

## Problema

Em 2019, um erro foi relatado ao Adobe Commerce que permitia que tentativas de logon com falha fossem registradas em um banco de dados no Adobe Commerce 2.3.x e 2.2.x. Em resposta, a Adobe Commerce incluiu uma correção para esse problema no Adobe Commerce 2.3.3 e 2.2.10 (lançado em outubro de 2019). Embora a correção desse erro tenha interrompido o registro de tentativas de logon com falha, as informações coletadas antes da atualização para essas versões atuais ainda podem existir. A correção mais recente apaga as informações de tentativas de logon registradas anteriormente, se houver.   O CVE-2019-8118 é descrito e rastreado em [Vulnerabilidades e Exposições Comuns](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Solução

Se você precisa usar o script anexado e o patch ou apenas o script, depende da sua versão do Adobe Commerce:

**Adobe Commerce e Magento Open Source versões 2.3.0-2.3.2-p2**

Para essas versões, você deve aplicar o patch e executar o script de limpeza do banco de dados anexado para encerrar o registro contínuo e eliminar logs.

1. Execute o patch do compositor para parar o registro. Este patch está anexado ao artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no seguinte link [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Para obter instruções sobre como aplicar o patch, consulte [Como aplicar um patch compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de suporte.

1. Agora execute o script para limpar o banco de dados das tentativas de logon com falha pré-existentes. Este script é anexado ao artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no seguinte link [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Consulte a seção [**Como executar o script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) para obter instruções.

**Adobe Commerce e Magento Open Source versões 2.3.3 e posteriores/2.2.10 e posteriores**<br>
Para essas versões somente, execute o script abaixo para limpar registros antigos (o registro foi encerrado anteriormente para essas versões por meio de uma correção lançada em outubro de 2019). Este script é anexado ao artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no seguinte link [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Consulte a seção [**Como executar o script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) da nossa base de dados de conhecimento de suporte para obter instruções.

**Como executar o script**

Siga as instruções abaixo para executar o script:

1. Coloque `DB_CLEANUP_SCRIPT_v2.php` no diretório raiz da instalação do Adobe Commerce ou Magento Open Source (no mesmo diretório do aplicativo que contém `app/bootstrap.php`).
1. Execute este comando no terminal: `php DB_CLEANUP_SCRIPT_v2.php` e ele iniciará o processo de limpeza do banco de dados.

Se você encontrar problemas ao executar o script, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ou envie um email para [security@magento.com](mailto:security@magento.com).

**Arquivos anexados**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
