---
title: Data errada para preço especial
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.2 relacionado à data "de" do preço especial do produto que está incorreta se o valor for alterado pelo administrador cuja localidade da interface é diferente.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Data errada para preço especial

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.2 relacionado à data &quot;de&quot; do preço especial do produto que está incorreta se o valor for alterado pelo administrador cuja localidade da interface é diferente.

## Problema

Ao definir/alterar o preço especial de um produto, a data e a hora atuais são salvas no banco de dados como um valor para o atributo `special_from_date` (não visível ao editar um produto). Se você editar o preço especial e sua conta de usuário administrador for definida como uma localidade de interface diferente, um valor incorreto poderá ser definido como `special_from_date` devido aos problemas no formato de data de análise para localidades diferentes.

<u>Etapas a serem reproduzidas</u>:

Pré-requisitos: a localidade do usuário administrador é inglês (Estados Unidos).

1. Faça logon no Administrador do Commerce.
1. Vá para as configurações da conta de usuário administrador.
1. Defina a localidade da interface para ucraniano.
1. Clique em **Salvar Conta**.
1. Ir para **Catálogo** > **Produto**.
1. Selecione qualquer produto.
1. Na página do produto, clique em **Advanced Pricing**.
1. Adicione um preço especial.
1. Salve o produto.
1. Repita as etapas 7 a 9.
1. Vá para **Sistema** > **Logs de Ação**.
1. Verifique o log para obter atualizações de produto.

<u>Resultados esperados</u>:

A data inicial do preço especial deve ser a data atual.

<u>Resultados reais</u>:

A data de início do preço especial é uma data de alguns anos no futuro, impedindo que o preço especial esteja ativo.

## Solução

Aplicar o patch impedirá que o problema ocorra novamente. Para corrigir os dados dos produtos em que a data foi definida incorretamente, redefina o preço especial depois de aplicar o patch.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-11605\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce (todos os métodos de implantação) 2.2.2

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local 2.1.0 - 2.1.18, 2.2.0 - 2.2.5
* Adobe Commerce na infraestrutura em nuvem 2.1.11-2.1.18, 2.2.0-2.2.5

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
