---
title: Hotfix do pacote de compatibilidade do Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0
description: Este artigo fornece uma correção para adicionar compatibilidade ao novo [!DNL HIPAA] pacote 1.2.0 com o Adobe Commerce na infraestrutura em nuvem 2.4.7-p4
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Hotfix do pacote de compatibilidade do Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0

Este artigo fornece uma correção para adicionar compatibilidade ao novo pacote **[!DNL HIPAA]1.2.0** com o Adobe Commerce na infraestrutura na nuvem 2.4.7-p4.

O problema será corrigido na versão 2.4.7-p5.

## Versões e produtos afetados

Adobe Commerce na infraestrutura em nuvem 2.4.7-p4 e anterior

## Pré-requisitos

* A Adobe provisionou sua conta da Adobe Commerce para acessar a extensão **[!DNL HIPAA Ready]**. Consulte [[!DNL HIPAA] disponibilidade no Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) para obter mais detalhes no nosso **Adobe Commerce: Guia de Introdução**.
* Acesso ao [repo.magento.com](https://repo.magento.com) para instalar a extensão. Para obter a geração de chaves e obter os direitos necessários, consulte [Obter suas chaves de autenticação](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) em nosso **Guia de Instalação do Adobe Commerce**.

## Problema

O pacote 1.1.0 do [!DNL HIPAA] não é compatível com a linha de versão 2.4.7x do Adobe Commerce.

## Solução

Por meio desse hotfix, os comerciantes que executam o Adobe Commerce na infraestrutura na nuvem 2.4.7-p4 poderão usar o pacote [!DNL HIPAA] 1.2.0.

>[!NOTE]
>
>O **[!DNL HIPAA]1.2.0 é compatível somente com o Adobe Commerce 2.4.7-p5. Se quiser adicionar compatibilidade com o [!DNL HIPAA] 1.2.0 ao Adobe Commerce 2.4.7-p4, instale o patch fornecido.<br><u>Se você não estiver no Adobe Commerce 2.4.7-p4, é necessário primeiro atualizar para o Adobe Commerce 2.4.7-p4 para usar este patch</u>.**

Para corrigir o problema do Adobe Commerce na infraestrutura em nuvem 2.4.7-p4, você deve aplicar o patch:

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Como aplicar o patch

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

## Somente para comerciantes do Adobe Commerce na nuvem - Como saber se o patch foi aplicado

Considerando que não é possível verificar facilmente se o problema foi corrigido, talvez você queira verificar se o patch foi aplicado com sucesso.

>[!NOTE]
>
><u>Você pode fazer isso seguindo estas etapas, usando o arquivo `VULN-27015-2.4.7_COMPOSER.patch` **como um Exemplo**</u>:

1. [Instale a Ferramenta de Correções de Qualidade](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Executar o comando:<br>
   ![cve-2024-34102-tell-if-patch-plied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Você deve ver uma saída semelhante a esta, **<u>onde o Exemplo usado aqui, VULN-27015</u>**, retorna o status *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
