---
title: Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB24-73]
promoted: true
description: Aplique um patch Isolado para corrigir [!DNL critical, important, and moderate vulnerabilities] instâncias do Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 e versões anteriores que estejam executando apenas o módulo  [!DNL B2B] .
feature: Compliance, Security
role: Developer
source-git-commit: 483589be81e55f818f5cf93cccff2ffcbb5763cf
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB24-73]

Em 08 de outubro de 2024, o Adobe lançou uma atualização de segurança agendada regularmente para o Adobe Commerce e [!DNL Adobe Commerce Webhooks Plugin].
Esta atualização resolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilidades. A exploração bem-sucedida pode levar à execução arbitrária de código, à leitura arbitrária do sistema de arquivos, ao desvio de recursos de segurança e ao escalonamento de privilégios. O informativo é [Boletim de Segurança de Adobe ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

>[!NOTE]
>
>**[!DNL CVE-2024-45115], listado no boletim de segurança acima, é aplicável somente ao usar o módulo [!DNL B2B].** Para ajudar a garantir que a correção para esta vulnerabilidade possa ser aplicada o mais rápido possível, o Adobe também lançou um patch Isolado que resolve [!DNL CVE-2024-45115].

**Aplique as atualizações de segurança mais recentes assim que possível. Se você não conseguir fazer isso, estará vulnerável a esses problemas de segurança e o Adobe terá meios limitados para ajudar a remediar.**

>[!NOTE]
>
>Entre em contato com os Serviços de suporte se encontrar problemas ao aplicar o patch de segurança/patch isolado.

## Produtos e versões afetados

Adobe Commerce na nuvem e Adobe Commerce no local:

* 2.4.7-p2 e anterior
* 2.4.6-p7 e anterior
* 2.4.5-p9 e anterior
* 2.4.4-p10 e anterior

B2B:

* 1.4.2-p2 e anterior
* 1.3.5-p7 e anterior
* 1.3.4-p9 e anterior
* 1.3.3-p10 e anterior


## Solução para software Adobe Commerce na nuvem e Adobe Commerce no local

Para ajudar a resolver a vulnerabilidade dos produtos e versões afetados, aplique o patch Isolado [!DNL CVE-2024-45115].

## Detalhes do patch isolado

Use o seguinte patch isolado:

[vuln-26510-composer-patch.zip](assets/vuln-26510-composer-patch.zip)

## Como aplicar o patch Isolado

Descompacte o arquivo e consulte [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

## Somente para Adobe Commerce em comerciantes na nuvem - Como saber se os patches isolados foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, convém verificar se o patch Isolado [!DNL CVE-2024-45115] foi aplicado com êxito.

<u>Você pode fazer isso seguindo as etapas abaixo, usando o arquivo `VULN-27015-2.4.7_COMPOSER.patch` **como exemplo**</u>:

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

* [Boletim de Segurança de Adobe ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
