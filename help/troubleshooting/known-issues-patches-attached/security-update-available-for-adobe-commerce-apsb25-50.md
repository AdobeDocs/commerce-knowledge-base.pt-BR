---
title: Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB25-50]
promoted: true
description: Aplique um patch Isolado para corrigir [!DNL critical and important vulnerabilities] o Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13 e versões anteriores.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Atualização de segurança disponível para o Adobe Commerce - [!DNL APSB25-50]

Em 10 de junho de 2025, a Adobe lançou uma atualização de segurança programada regularmente para o Adobe Commerce e o Magento Open Source. Esta atualização soluciona as vulnerabilidades [[!DNL critical] e [!DNL important]](https://helpx.adobe.com/br/security/severity-ratings.html). A exploração bem-sucedida dessas vulnerabilidades pode levar ao desvio de recursos de segurança, escalonamento de privilégios e execução arbitrária de código.

Mais informações podem ser encontradas no [Boletim de Segurança do Adobe ([!DNL APSB25-50]) aqui](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

>[!NOTE]
>
>**Para ajudar a garantir que a correção de [!DNL CVE-2025-47110] listada no boletim de segurança acima, possa ser aplicada o mais rápido possível, a Adobe também lançou um patch isolado que resolve [!DNL CVE-2025-47110]. Isso permite que os comerciantes apliquem a correção isoladamente, com menos riscos de atraso devido a possíveis problemas de integração.**

**Aplique as atualizações de segurança mais recentes assim que possível. Se você não fizer isso, estará vulnerável a esses problemas de segurança, e a Adobe terá meios limitados para ajudar a corrigir o problema ainda mais.**

Você pode ler mais sobre [nosso processo de implantação de patch isolado aqui.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>Para clientes do Adobe Commerce no Managed Services, o seu engenheiro de sucesso do cliente pode fornecer orientação adicional sobre como aplicar o patch.

>[!NOTE]
>
>Entre em contato com os Serviços de suporte se encontrar problemas ao aplicar o patch de segurança/patch isolado.

Lembrando que você pode encontrar [as atualizações de Segurança mais recentes disponíveis para o Adobe Commerce aqui.](https://helpx.adobe.com/br/security/products/magento.html)

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação):

* 2.4.8
* 2.4.7-p5 e anterior
* 2.4.6-p10 e anterior
* 2.4.5-p12 e anterior
* 2.4.4-p13 e anterior

## Problemas

### I. CVE-2025-47110: XSS armazenado por injeção de modelo do lado do servidor no Adobe Commerce 2.4.7-p4

<u>Produtos e versões afetados</u>:

Adobe Commerce (todos os métodos de implantação):

* 2.4.8
* 2.4.7-p5 e anterior
* 2.4.6-p10 e anterior
* 2.4.5-p12 e anterior
* 2.4.4-p13 e anterior

<u>Solução</u>:

Para versões do Adobe Commerce:

* 2.4.8
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p10
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12, 2.4.4-p13

**Aplique o patch isolado a seguir ou atualize para o patch de segurança mais recente.**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547: XSS refletido em marketplace.magento.com + problema ATO de um clique que afeta instâncias IMS

<u>Produtos e versões afetados</u>:

Adobe Commerce (todos os métodos de implantação):

* 2.4.8

<u>Solução</u>:

Para versões do Adobe Commerce:

* 2.4.8

**Aplique o patch isolado a seguir ou atualize para o patch de segurança mais recente.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Como aplicar o patch Isolado

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=pt-BR) em nossa base de dados de suporte para obter instruções.

## Somente para Adobe Commerce em comerciantes na nuvem - Como saber se os patches isolados foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, você pode querer verificar se o patch isolado [!DNL CVE-2025-47110] foi aplicado com sucesso.

>[!NOTE]
>
><u>Você pode fazer isso seguindo as etapas abaixo, usando o arquivo `VULN-27015-2.4.7_COMPOSER.patch` **como EXEMPLO**</u>:

1. [Instale a Ferramenta de Correções de Qualidade](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR).
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

* [Boletim de Segurança do Adobe ([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [As atualizações de Segurança mais recentes disponíveis para o Adobe Commerce](https://helpx.adobe.com/br/security/products/magento.html)
