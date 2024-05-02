---
title: Adobe Commerce de erros de trabalho do CRON do relatório avançado
description: Este artigo fornece patches para os problemas dos trabalhos cron do Relatórios avançados no Adobe Commerce, que pode causar um erro 404 para clientes que tentam acessar os Relatórios avançados.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce de erros de trabalho do CRON do relatório avançado

Este artigo fornece patches para os problemas dos trabalhos cron do Relatórios avançados no Adobe Commerce, que pode causar um erro 404 para clientes que tentam acessar os Relatórios avançados.

## Produtos e versões afetados

Adobe Commerce (todas as opções de implantação) 2.3.x

## Problema

Um cliente recebe um erro 404 ao tentar acessar os Relatórios avançados e há erros nos logs associados ao `analytics_collect_data job` .

## Versões compatíveis do Magento:

Os patches são compatíveis (mas podem não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (todas as opções de implantação) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (todas as opções de implantação) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (todas as opções de implantação) 2.3.0

## **Solução**

Para corrigir o problema, aplique a correção relevante anexada a este artigo. Para baixá-lo, clique nos links a seguir:

* Baixar [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Baixar [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Baixar [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

Para verificar qual patch usar:

<ol><li>Revise os logs usando o seguinte comando:<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>Dependendo do erro exibido, selecione um patch usando as informações da tabela a seguir.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Erro</p>
</td>
<td class="wysiwyg-text-align-center">Correção</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: erro ao executar um trabalho cron {"exception":"[object] (RuntimeException(code: 0): erro ao executar um trabalho cron em /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327, TypeError(code: 0): substr_count() espera que o parâmetro 1 seja uma cadeia de caracteres, nulo fornecido em /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"} []</pre>OU<pre>report.ERROR: Cron Job analytics_collect_data tem um erro: substr_count() espera que o parâmetro 1 seja uma cadeia de caracteres, nulo fornecido. Estatísticas: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Aplicar<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>, limpe o cache e aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.</td>
</tr>
<tr>
<td>
<p><em>Falha ao abrir o arquivo /tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/.../</em></p>
</td>
<td>Aplicar<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>, limpe o cache e aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.</td>
</tr>
<tr>
<td><em>Criptografia inválida</em></td>
<td>Aplicar<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>, limpe o cache e aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.</td>
</tr>
</tbody>
</table>
</li></ol>

## Como aplicar o patch

Descompacte o arquivo e siga as instruções em [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Leitura relacionada

[O arquivo não pode ser excluído. Aviso!unlink: erro de arquivo ou diretório inexistente no Administrador](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
