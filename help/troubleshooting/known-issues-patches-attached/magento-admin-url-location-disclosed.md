---
title: Localização do URL de administração do Adobe Commerce divulgada
description: Este artigo fornece uma correção para o problema de segurança do Adobe Commerce, no qual a localização do URL do painel do Administrador pode ser revelada. Conhecer a localização do URL pode facilitar a automatização de ataques.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Localização do URL de administração do Adobe Commerce divulgada

Este artigo fornece uma correção para o problema de segurança do Adobe Commerce, no qual a localização do URL do painel do Administrador pode ser revelada. Conhecer a localização do URL pode facilitar a automatização de ataques.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.X.X
* Adobe Commerce no local 2.X.X
* Magento Open Source 2.X.X

## Problema

Foi descoberto um problema no Magento Open Source e no Adobe Commerce que pode ser usado para revelar a localização do URL do painel do Administrador. Embora atualmente não haja motivos para acreditar que esse problema resultaria diretamente em comprometimento, saber a localização do URL pode facilitar a automatização dos ataques.

## Solução

Para corrigir o problema, aplique a correção anexada a este artigo. Para baixá-lo, clique no link a seguir:

* Baixar [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - para versões 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Baixar [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - para as versões 2.2.0-2.2.8, todas as edições
* Baixar [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - para as versões 2.3.0-2.3.1, todas as edições

Se você não vir um patch para o seu produto/versão, atualize para a versão de segurança mais recente e aplique o patch.

Adobe recomenda fortemente aplicar o patch o mais rápido possível, mesmo que você não tenha experimentado quaisquer sintomas de uma crise.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Outras recomendações de segurança

A Adobe também recomenda que os comerciantes implantem ferramentas para proteger seu painel de administração, incluindo autenticação de dois fatores, VPN, Incluir na lista de permissões IP e muito mais. Para obter informações detalhadas, consulte os seguintes blogs e documentação:

* [5 Ações Imediatas para o Protect contra Ataques à Força Bruta](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect Sua Senha De Instalação Do Magento Adivinhando Nova Atualização](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Práticas recomendadas de segurança](https://magento.com/security/best-practices/security-best-practices)
* Adicionando e Configurando a Autenticação de Dois Fatores no Adobe Commerce para [2.4.x](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
