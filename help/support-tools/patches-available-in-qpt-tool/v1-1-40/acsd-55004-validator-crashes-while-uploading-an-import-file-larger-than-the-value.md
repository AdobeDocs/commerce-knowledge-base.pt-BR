---
title: 'ACSD-55004: O validador falha ao carregar um arquivo de importação maior que o valor'
description: Aplique o patch ACSD-55004 para corrigir o problema do Adobe Commerce em que um validador falha ao carregar um arquivo de importação maior que o valor configurado em &grave;php.ini&grave;.
feature: Data Import/Export
role: Admin, Developer
exl-id: 03b7667e-9b5b-4319-9135-dbc7fda7861d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-55004: O validador falha ao carregar um arquivo de importação maior que o valor

O patch ACSD-55004 corrige o problema em que um validador falha ao carregar um arquivo de importação maior que o valor configurado em `php.ini`. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.40 está instalado. A ID do patch é ACSD-55004. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O validador falha ao carregar um arquivo de importação maior que o valor configurado em `php.ini`.

<u>Etapas a serem reproduzidas</u>:

Tente carregar um arquivo de importação maior do que o configurado em `php.ini`.

<u>Resultados esperados</u>:

O tamanho do arquivo é validado sem erros.

<u>Resultados reais</u>:

O validador trava.

`var/log/exception.log` contém:

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
