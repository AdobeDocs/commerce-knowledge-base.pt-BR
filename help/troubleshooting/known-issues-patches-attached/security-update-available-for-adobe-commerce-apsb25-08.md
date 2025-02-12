---
title: Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Aplique um patch Isolado para corrigir [!DNL critical, important, and moderate vulnerabilities] o Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 e versões anteriores.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: babb822cc505e2911ae28cd1a2540799146f19b3
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB25-08]

Em 11 de fevereiro de 2025, a Adobe lançou uma atualização de segurança programada regularmente para o Adobe Commerce e o Magento Open Source. Esta atualização resolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilidades. A exploração bem-sucedida dessas vulnerabilidades pode levar à execução arbitrária de código, ao desvio de recursos de segurança e à escalada de privilégios. Mais informações podem ser encontradas no [Boletim de Segurança do Adobe ([!DNL APSB25-08]) aqui](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Para ajudar a garantir que a correção de [!DNL CVE-2025-24434], listada no boletim de segurança acima, possa ser aplicada o mais rápido possível, a Adobe também lançou um patch isolado que resolve [!DNL CVE-2025-24434]. Isso permite que os comerciantes apliquem a correção isoladamente, com menos riscos de atraso devido a possíveis problemas de integração.**

**Aplique as atualizações de segurança mais recentes assim que possível. Se você não fizer isso, estará vulnerável a esses problemas de segurança, e a Adobe terá meios limitados para ajudar a corrigir o problema ainda mais.**

>[!NOTE]
>
>Entre em contato com os Serviços de suporte se encontrar problemas ao aplicar o patch de segurança/patch isolado.

## Produtos e versões afetados

Infraestrutura do Adobe Commerce na nuvem, Adobe Commerce no local e Magento Open Source:

* 2.4.8-beta1 e anterior
* 2.4.7-p3 e anterior
* 2.4.6-p8 e anterior
* 2.4.5-p10 e anterior
* 2.4.4-p11 e anterior

## Solução para software Adobe Commerce na nuvem, Adobe Commerce no local e Magento Open Source

Para ajudar a resolver a vulnerabilidade dos produtos e versões afetados, você deve aplicar o patch Isolado do [!DNL CVE-2025-24434], dependendo da sua versão do Adobe Commerce/Magento Open Source.

## Detalhes do patch isolado

Use os seguintes patches isolados anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

### Para a versão 2.4.8-beta1:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### Para as versões 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### Para as versões 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### Para as versões 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### Para as versões 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Como aplicar o patch Isolado

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

## Somente para Adobe Commerce em comerciantes na nuvem - Como saber se os patches isolados foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, convém verificar se o patch Isolado [!DNL CVE-2025-24434] foi aplicado com êxito.

>[!NOTE]
>
><u>Você pode fazer isso seguindo as etapas abaixo, usando o arquivo `VULN-27015-2.4.7_COMPOSER.patch` **como exemplo**</u>:

1. [Instale a Ferramenta de Correções de Qualidade](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Executar o comando:<br>
   ![cve-2024-34102-tell-if-patch-plied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Você deve ver uma saída semelhante a esta, onde VULN-27015 retorna o status *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Atualizações de segurança

Atualizações de segurança disponíveis para o Adobe Commerce:

* [Boletim de Segurança do Adobe ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [As atualizações de Segurança mais recentes disponíveis para o Adobe Commerce)](https://helpx.adobe.com/security/products/magento.html)
