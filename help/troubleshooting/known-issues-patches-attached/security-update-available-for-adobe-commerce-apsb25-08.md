---
title: Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Aplique um patch Isolado para corrigir [!DNL critical, important, and moderate vulnerabilities] tanto para Adobe Commerce quanto para Magento Open Source 2.4.7-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 e versões anteriores.
feature: Compliance, Security
role: Developer
source-git-commit: 45c6486dea10b37aa8114467bbd7be0c7f9f86f6
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB25-08]

Em 11 de fevereiro de 2025, o Adobe lançou uma atualização de segurança programada regularmente para o Adobe Commerce e o Magento Open Source. Esta atualização resolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilidades. A exploração bem-sucedida dessas vulnerabilidades pode levar à execução arbitrária de código, ao desvio de recursos de segurança e à escalada de privilégios. Mais informações podem ser encontradas no [Boletim de Segurança do Adobe ([!DNL APSB25-08]) aqui](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Para ajudar a garantir que a correção para [!DNL CVE-2025-24434], listada no boletim de segurança acima, possa ser aplicada o mais rápido possível, o Adobe também lançou um patch isolado que resolve [!DNL CVE-2025-24434]. Isso permite que os comerciantes apliquem a correção isoladamente, com menos riscos de atraso devido a possíveis problemas de integração.**

**Aplique as atualizações de segurança mais recentes assim que possível. Se isso não for possível, você estará vulnerável a esses problemas de segurança e o Adobe terá meios limitados para ajudar a corrigir o problema ainda mais.**

>[!NOTE]
>
>Entre em contato com os Serviços de suporte se encontrar problemas ao aplicar o patch de segurança/patch isolado.

## Produtos e versões afetados

Infraestrutura do Adobe Commerce na nuvem, Adobe Commerce no local e Magento Open Source:

* 2.4.7-beta1 e anterior
* 2.4.7-p3 e anterior
* 2.4.6-p8 e anterior
* 2.4.5-p10 e anterior
* 2.4.4-p11 e anterior

## Solução para software Adobe Commerce na nuvem e Adobe Commerce no local

Para ajudar a resolver a vulnerabilidade dos produtos e versões afetados, aplique o patch Isolado [!DNL CVE-2025-24434].

## Detalhes do patch isolado

Use o seguinte patch isolado:

[vuln-28982-composer-patch.zip](assets/vuln-28982-composer-patch.zip)

## Como aplicar o patch Isolado

Descompacte o arquivo e consulte [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

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

* [Boletim de Segurança de Adobe ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [As atualizações de Segurança mais recentes disponíveis para o Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)
