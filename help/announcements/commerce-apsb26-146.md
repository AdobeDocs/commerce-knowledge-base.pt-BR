---
title: Ação urgente Atualização de segurança crítica necessária disponível para o Adobe Commerce (APSB26-146)
description: A Adobe lançou o Boletim de segurança APSB26-146 que aborda o CVE-2026-75650, uma vulnerabilidade de dia zero no Adobe Commerce. Saiba como aplicar o hotfix e girar credenciais.
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: e95fb4ca696be9f6d348ff66196565797575f74a
workflow-type: tm+mt
source-wordcount: 954
ht-degree: 0%

---


# Ação urgente necessária: atualização de segurança crítica disponível para o Adobe Commerce (APSB26-146)

>[!IMPORTANT]
>
>Esta é uma atualização urgente relacionada ao CVE-2026-75650. A Adobe está ciente de que o CVE-2026-75650 foi explorado na natureza e direcionado aos comerciantes do Adobe Commerce.

Em 7 de setembro, a Adobe lançou uma atualização de segurança crítica que afeta o Adobe Commerce e o Magento Open Source. A Adobe tomou conhecimento de uma vulnerabilidade &quot;dia zero&quot; no Adobe Commerce e lançou uma atualização de segurança (APSB26-146) para resolvê-la. A vulnerabilidade pode permitir que um invasor não autenticado execute código arbitrário em uma instalação afetada (CVE-2026-75650).

A Adobe lançou o Boletim de segurança APSB26-146, que aborda essa vulnerabilidade. O boletim está disponível aqui:

[Atualização de segurança disponível para o Adobe Commerce | APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

Este artigo explica como aplicar o hotfix das versões atuais e anteriores do Adobe Commerce e do Magento Open Source.

## Descrição

Produtos e versões afetados:

Versões do Adobe Commerce:

* 2.4.9-2026-ago e anterior
* 2.4.8-2026-ago e anterior
* 2.4.7-2026-ago e anterior
* 2.4.6-2026-ago e anterior
* 2.4.5-2026-ago e anterior
* 2.4.4-2026-ago e anterior

Versões B2B do Adobe Commerce:

* 1.5.3-2026-ago e anterior
* 1.5.2-2026-ago e anterior
* 1.4.2-2026-ago e anterior
* 1.3.4-2026-ago e anterior
* 1.3.3-2026-ago e anterior

Versões do Magento Open Source:

* 2.4.9-2026-ago e anterior
* 2.4.8-2026-ago e anterior
* 2.4.7-2026-ago e anterior
* 2.4.6-2026-ago e anterior

## Resolução

### Solução para Adobe Commerce na nuvem, Adobe Commerce no local e Magento Open Source

>[!NOTE]
>
>O hotfix do CVE-2026-75650 agora é compatível com todas as versões de Adobe Commerce e Magento Open Source entre 2.4.4 e 2.4.7. Consulte a tabela abaixo e baixe o patch aplicável à sua versão.

Para ajudar a resolver a vulnerabilidade dos produtos e versões afetados, aplique o **patch abaixo** (dependendo da sua versão) e gire suas chaves de criptografia.

| Número da versão | Correção |
|---|---|
| 2.4.9-2026-ago, 2.4.8-2026-ago, 2.4.7-2026-ago, 2.4.6-2026-ago, 2.4.5-2026-ago, 2.4.4-2026-ago, 2.4.9-2026-jul, 2.4.8-2026-jul, 2.4.7-2026-jul, 2.4.6-2026-jul, 2.4.5-2026-jul, 2.4.4-2026-jul, 2.4.8-p5, 2.4.8-p4, 2.4.8-p3, 2.4.7-p10, 2.4.7-p9, 2.4.6-p15, 2.4.6-p14, 2.4.5-p17, 2.4.5-p16, 2.4.4-p18, 2.4.4-p17 | [Hotfix VULN-39341-composer-patches.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip) |
| 2.4.8-p3, 2.4.8-p2 | [VULN-39341_248-p3.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p3-patch.zip) |
| 2.4.8-p1, 2.4.8 | [VULN-39341_248-p1.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p1-patch.zip) |
| 2.4.7-p8, 2.4.7-p7 | [VULN-39341_247-p8.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p8-patch.zip) |
| 2.4.7 - 2.4.7-p6 | [VULN-39341_247-p5.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p5-patch.zip) |
| 2.4.6-p13, 2.4.6-p12, 2.4.5-p15, 2.4.5-p14, 2.4.4-p16, 2.4.4-p15 | [VULN-39341_246-p13.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p13-patch.zip) |
| 2.4.6 - 2.4.6-p11, 2.4.5 - 2.4.5-p13, 2.4.4 - 2.4.4-p14 | [VULN-39341_246-p11.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p11-patch.zip) |


{style="table-layout:auto"}

### Como aplicar o hotfix

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) em nossa base de dados de suporte para obter instruções.

### Confirmar se a correção foi aplicada (somente Adobe Commerce em comerciantes da nuvem)

Considerando que não é possível determinar facilmente se o problema foi corrigido, recomenda-se verificar se a correção CVE-2026-75650 foi aplicada com êxito.

Você pode fazer isso seguindo as etapas abaixo, usando o arquivo `VULN-39341_Hotfix_COMPOSER.patch` como exemplo:

1. [Instale a Ferramenta de Correções de Qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage#install).
1. Execute o comando: `vendor/bin/magento-patches -n status | grep "39341\|Status"`.
1. Você deve ver uma saída semelhante a esta, em que este exemplo VULN-39341 retorna o status Aplicado:

| ID | Título | Categoria | Origem | Status | Detalhe |
|---|---|---|---|---|---|
| N/D | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | Outro | Local | Aplicado | Tipo de patch: personalizado |

### Girar as credenciais após aplicar o patch

Para corrigir totalmente esse problema, gire não apenas sua chave de criptografia, mas todas as credenciais que possam ter sido criptografadas ou expostas usando-a, incluindo credenciais de servidor, API e integração.

>[!NOTE]
>
>A chave de criptografia é usada para criptografar tokens de integração, credenciais de gateway de pagamento e tokens de automação com privilégios de sistema. Girar a chave de criptografia sozinha não invalida as credenciais que podem já ter sido expostas. Gire todas as credenciais associadas em sua origem (por exemplo, no gateway de pagamento ou serviço de terceiros), não apenas no Commerce.

Para girar as credenciais, siga estas etapas:

1. Aplique o hotfix.
1. Ativar modo de manutenção.
1. Desabilite a execução do cron (comando Commerce on Cloud: `vendor/bin/ece-tools cron:disable`).
1. [Girar suas chaves de criptografia](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key?lang=en).
1. Girar todas as senhas de usuário do painel Administrador.
1. Desativar e regenerar todos os tokens de integração REST/SOAP/GraphQL (**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**).
1. Gire os segredos do cliente OAuth para qualquer aplicativo de terceiros conectado.
1. Alterne as credenciais da API do gateway de pagamento no nível do provedor (Stripe, Braintree, Adyen, PayPal etc.).
1. Girar credenciais do banco de dados.
1. Gire as chaves SSH/deploy e qualquer credencial de conta de serviço privilegiada do CRON ou do sistema.
1. Alterne as chaves da API para envio, impostos e outras extensões integradas de terceiros.
1. Limpe o cache.
1. Habilitar execução de cron (comando Commerce on Cloud: `vendor/bin/ece-tools cron:enable`).
1. Desabilitar modo de manutenção.
1. Somente Commerce na nuvem: reimplante para aplicar novas credenciais de banco de dados.

### Atualizações de segurança

Atualizações de segurança disponíveis para o Adobe Commerce:

* [Boletim de segurança do Adobe (APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [As atualizações de segurança mais recentes disponíveis para o Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)

### Leitura relacionada

[Habilite ou desabilite o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en) no Guia de Instalação do Adobe Commerce
