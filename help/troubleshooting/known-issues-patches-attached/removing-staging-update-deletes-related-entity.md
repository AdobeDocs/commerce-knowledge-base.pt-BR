---
title: A remoção da atualização de preparo exclui a entidade relacionada
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.3 relacionado à entidade (categoria, página do CMS etc.) sendo removido quando a atualização de agendamento relacionada for excluída.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# A remoção da atualização de preparo exclui a entidade relacionada

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.3 relacionado à entidade (categoria, página do CMS etc.) sendo removido quando a atualização de agendamento relacionada for excluída.

>[!NOTE]
>
>O problema foi corrigido no Adobe Commerce 2.2.6.

## Problema

Ao excluir uma atualização de agendamento ativa entre suas datas inicial e final, a entidade relacionada (categoria, subcategoria, página CMS) também é excluída.

<u>Etapas a serem reproduzidas (com categorias)</u>:

1. Faça logon no Administrador do Commerce.
1. Crie uma nova subcategoria em **Catálogo** > **Categorias**.
1. Crie uma nova Atualização de preparo com a hora de início e término.
1. Aguarde até que a atualização seja aplicada; essa é a hora de início.
1. Exclua a atualização usando o **Exibir/Editar** link.

<u>Resultados esperados</u>:

A atualização é excluída e a subcategoria ainda existe no Administrador.

<u>Resultados reais</u>:

A atualização e a subcategoria são excluídas.

## Solução

Aplique o patch fornecido neste artigo e limpe o cache em execução

```bash
bin/magento
  cache:clean
```

## Correção

Os patches estão anexados a este artigo. Para baixar um patch, role até o final do artigo e clique no nome do arquivo ou no link correspondente:

* [Baixar MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [Baixar MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [Baixar MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Versões compatíveis do Adobe Commerce:

Os patches foram criados para:

* MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch foi criado para o Adobe Commerce (todos os métodos de implantação) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch foi criado para o Adobe Commerce (todos os métodos de implantação) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch foi criado para o Adobe Commerce (todos os métodos de implantação) 2.2.5

O patch MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local 2.2.0 - 2.2.2
* Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.3

O patch MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local 2.1.0 - 2.1.18, 2.2.0 - 2.2.3
* Adobe Commerce na infraestrutura em nuvem 2.1.0 - 2.1.18, 2.2.0 - 2.2.3

O patch MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.2.5

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
