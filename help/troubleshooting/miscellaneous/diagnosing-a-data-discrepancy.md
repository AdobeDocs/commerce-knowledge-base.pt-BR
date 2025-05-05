---
title: Diagnosticando uma discrepância de dados
description: Este artigo fornece soluções para solucionar discrepâncias entre um relatório de Magento Business Intelligence (MBI) e uma consulta ou relatório de terceiros.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Diagnosticando uma discrepância de dados

Este artigo fornece soluções para solucionar discrepâncias entre um relatório de Magento Business Intelligence (MBI) e uma consulta ou relatório de terceiros.

Dependendo da complexidade da análise, gerar o relatório de MBI correspondente pode exigir familiaridade com vários aspectos diferentes da plataforma. Essa lista de verificação e os links relacionados ajudarão você a entender a lógica por trás do relatório, permitindo identificar a origem de qualquer discrepância.

1. Se outro membro da sua equipe criou o relatório, comece confirmando o objetivo e os parâmetros de sua análise.
1. Gere pontos de dados esperados para comparar ao relatório do MBI com base em uma consulta, uma ferramenta de relatório de terceiros ou uma fórmula.
1. Revise e confirme as definições de [métrica](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html?lang=pt-BR), seja a partir do link de métrica no Report Builder ou visitando a guia [Resumo do Sistema](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary):
   * Tabela de dados
   * Operação
   * Coluna operando, incluindo seu cálculo se for derivado (por meio do Resumo do Sistema)
   * Carimbo de data e hora
   * Para métricas de subscrição: datas de início e término
   * Filtros, incluindo aqueles contidos em qualquer [conjunto de filtros](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html?lang=pt-BR) aplicados
1. Revise e confirme outras manipulações de dados no relatório:
   * Fórmula calculada
   * [Agrupamentos](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=pt-BR#groupby)
   * [Perspectivas](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=pt-BR)
   * [Opções de tempo](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=pt-BR)
   * Para [análise de coorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): data de coorte
   * Para [análise de coorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): perspectiva de coorte
1. Se a discrepância envolver dados recentes, confirme o último ponto de dados disponível consultando a seção **Atualizar Detalhes** na página Conexões.
1. Se uma métrica usada na análise for criada em uma tabela do banco de dados em que as linhas são excluídas dessa tabela, confirme com a Equipe de suporte do MBI se a tabela está sendo verificada em busca de linhas excluídas, bem como a frequência da nova verificação e o [método de replicação](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html?lang=pt-BR) da tabela.
1. Da mesma forma, se as colunas usadas na análise puderem ser modificadas depois que uma linha for adicionada, confirme com o suporte que essas colunas estão sendo [verificadas em busca de modificações](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html?lang=pt-BR), bem como a frequência da nova verificação.

**Ainda está com problemas?** Não se preocupe, estamos aqui para ajudar. Enviar uma solicitação usando [estas instruções](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
