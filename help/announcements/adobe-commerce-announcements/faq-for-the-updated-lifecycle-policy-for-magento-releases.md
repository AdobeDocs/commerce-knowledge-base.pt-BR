---
title: Perguntas frequentes sobre a política de ciclo de vida atualizada para versões do Adobe Commerce
description: 'A Adobe Commerce fornece correções de qualidade para uma versão secundária por um mínimo de 12 meses a partir da data de disponibilidade geral da próxima versão secundária de software. A maneira como fornecemos correções de qualidade durante esse período está mudando:'
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: f11596ea844fead42141c7e1fea586b2a11f757a
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---

# Perguntas frequentes sobre a política de ciclo de vida atualizada para versões do Adobe Commerce

## O que está mudando?

A Adobe Commerce fornece correções de qualidade para uma versão secundária por um mínimo de 12 meses a partir da data de disponibilidade geral da próxima versão secundária de software. A maneira como fornecemos correções de qualidade durante esse período está mudando:

* **Política anterior:** Atualmente, as correções de qualidade para a linha anterior que está na janela de EOS de 12 meses são entregues por meio da versão de patch trimestral, tornando os patches trimestrais uma combinação de segurança + qualidade.
* **Nova política:** a partir da versão 2.4 como a linha de versão secundária mais atual, os patches de versão da linha com suporte anterior (2.3) serão movidos para somente segurança. Ainda forneceremos correções de qualidade para a linha compatível anterior durante a janela de 12 meses após o lançamento de uma versão secundária (como 2.4) e novas linhas de versão secundárias subsequentes; mas elas serão disponibilizadas por meio da [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) e estarão focalizadas apenas em problemas críticos.

## Quando esta política entra em vigor?

O Adobe Commerce 2.3.6 está programado para ser lançado em 15 de outubro de 2020 e está planejado para ser a última versão de patch para o Adobe Commerce 2.3 que incluirá qualidade + segurança. Após a versão 2.3.6, a linha 2.3.x se tornará somente segurança, e problemas de qualidade críticos para a versão 2.3 poderão ser corrigidos via QPT.

>[!NOTE]
>
>A única vez que lançaremos uma versão completa da 2.3 é se precisarmos manter a conformidade com nossa pilha de tecnologia, como para PHP ou Elasticsearch. Isto está acontecendo no segundo trimestre de 2021 com uma atualização obrigatória do PHP 7.4, nós iremos incrementar a linha para 2.3.7. Para obter detalhes, consulte a publicação [Suporte ao PHP 7.4 para Adobe Commerce versão 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog.

## O que é uma versão somente de segurança?

As versões somente de segurança contêm apenas correções de segurança e nenhuma qualidade foi corrigida. Observe, no entanto, que nossas versões somente de segurança podem incluir hot fixes específicos quando consideramos que eles são absolutamente essenciais para executar o Adobe Commerce.

## Ainda haverá uma versão somente de segurança para a linha mais recente (a partir da publicação, 2.4)?

A Adobe também continuará a ter versões somente de segurança para a linha de versão mais recente. O processo para isso está descrito em [Introdução à Nova Versão de Patch Somente de Segurança](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) na publicação do DevBlog.

## O que é a Ferramenta de correção de qualidade?

Consulte o artigo [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) em nossa base de dados de conhecimento de suporte.

## Quem deve considerar o uso dessa nova política?

A nova política tem como objetivo criar caminhos para os comerciantes planejarem estrategicamente os custos anuais de desenvolvimento do Adobe Commerce, permitindo que eles mantenham a segurança e a qualidade crítica durante esses ciclos estratégicos. Ele também pode ser utilizado por comerciantes que se preocupam com a segurança sobre tudo o resto e estão geralmente satisfeitos com a estabilidade da linha mais antiga e suportada. Os comerciantes podem achar mais fácil planejar e orçar essas atualizações, pois elas serão mais previsíveis.

## Os comerciantes ainda devem atualizar para a linha mais recente?

Em última análise, todos os comerciantes ainda devem priorizar o planejamento para adotar a linha Adobe Commerce mais recente em tempo hábil. A nova linha Security Only e a ferramenta QPT não se destinam a suplantar o roteiro de atualização estratégica para os comerciantes; em vez disso, oferecem flexibilidade aos comerciantes no planejamento de seu roteiro de atualização e um meio de reagir rapidamente a problemas de segurança/qualidade sem precisar implementar uma atualização completa.

## Como receberei correções de qualidade em versões secundárias compatíveis que não sejam a linha mais recente?

As correções serão disponibilizadas por meio da [Ferramenta de correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).

## Como obterei correções de qualidade na linha mais recente?

A linha atual terá qualidade como parte da atualização trimestral. Entre as versões, se você entrar em contato com o suporte para uma correção na linha mais recente, eles a fornecerão via QPT. Em seguida, uma vez atualizado para a versão que tem essa correção, ela será aplicada por meio do patch trimestral.

## Que tipo de problemas de qualidade serão corrigidos em versões secundárias compatíveis que não sejam a linha mais recente?

Somente problemas de qualidade importantes que interrompem os fluxos principais serão corrigidos na linha anterior (2.3) e entregues via QPT.

## Alguma correção de qualidade fará parte da versão trimestral das versões secundárias compatíveis que não forem a linha mais recente?

Sim, como parte da linha somente segurança, lançamos o que a Adobe chama de &quot;hot fixes&quot; para essa linha. Esses são problemas altamente críticos que afetam o aplicativo Adobe Commerce.

## As melhorias de segurança e o QPT serão fornecidos ao mesmo tempo?

A linha somente de segurança seguirá a programação de lançamento trimestral e será lançada com a nomenclatura -p1. Exemplo 2.3.6-p1. A qualidade será lançada ad hoc à medida que os problemas de qualidade forem descobertos e corrigidos, e eles serão disponibilizados via QPT.

## Se eu tiver um problema de qualidade que não será resolvido nas versões secundárias suportadas que não são a linha mais recente ou QPT, o que devo fazer?

A linha anterior sendo apenas de segurança significa que o principal benefício é manter-se seguro. Somente patches para problemas graves que interrompem os fluxos principais serão disponibilizados por meio do QPT.

Problemas que não afetam os fluxos principais ou têm soluções alternativas serão corrigidos somente na linha mais recente. A Adobe incentiva os usuários que desejam correções críticas e não críticas a avançarem para a linha mais recente.

## As atualizações serão mais caras ou difíceis para os comerciantes se permanecerem na linha somente de segurança até que o suporte de segurança seja encerrado?

Em teoria, eles devem ser iguais em custo para o comerciante em termos de horas de desenvolvimento, desde que não tenham adotado um grande número de patches de qualidade. Se um comerciante descobrir que precisa ou deseja mais do que alguns patches por meio da ferramenta QPT, a recomendação é que ele priorize uma atualização para a versão mais recente do Adobe Commerce. A adoção de um grande número de Patches de qualidade, em vez de atualizar para a versão atual do Adobe Commerce, pode aumentar os custos de desenvolvimento e as complexidades da atualização assim que a linha somente de segurança chegar ao fim do suporte.

## Por que devo limitar a quantidade de patches de qualidade entregues via QPT?

Ao aplicar muitas correções de qualidade individuais, você torna seu código do Adobe Commerce mais complexo. A complexidade adicional pode resultar em alterações imprevisíveis ao atualizar para a linha de versão mais recente. É por isso que recomendamos usar o QPT com moderação e apenas para as correções mais críticas.

## E quanto à conformidade para pilhas de tecnologia?

Durante o tempo de vida de uma linha de lançamento, haverá atualizações para várias pilhas de tecnologia como PHP ou Elasticsearch que precisarão ser atualizadas para se manterem compatíveis. Daremos o máximo de aviso possível aos nossos comerciantes que eles estão chegando.

Observação: no segundo trimestre de 2021, precisaremos atualizar o PHP e o Redis na linha 2.3.x para permanecermos compatíveis. Isso fará com que a linha incremente para 2.3.7. Para obter detalhes, consulte a publicação [Suporte ao PHP 7.4 para Adobe Commerce versão 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog.
