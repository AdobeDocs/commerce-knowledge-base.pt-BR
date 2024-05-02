---
title: Adobe Commerce Recommendations para vulnerabilidades do PHP
description: No dia 3 de setembro, o Centro de Análise e Compartilhamento de Informações de Vários Estados (MS-ISAC) emitiu um alerta relacionado a várias vulnerabilidades que podem permitir a execução arbitrária de código e uma recomendação para que todos os sites que usam PHP atualizem para a versão mais recente do PHP o quanto antes ([alerta completo está disponível aqui](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Adobe Commerce Recommendations para vulnerabilidades do PHP

Em 3 de setembro, o Centro de Análise e Compartilhamento de Informações Multisestado (MS-ISAC) emitiu um alerta relacionado a múltiplas vulnerabilidades que podem permitir a execução arbitrária de código e uma recomendação para que todos os sites que usam PHP devem atualizar para a versão mais recente do PHP o quanto antes ([alerta completo disponível aqui](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>No Adobe Commerce na infraestrutura em nuvem, observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando o upgrade de serviço necessário e informando o horário em que você deseja que o processo de upgrade tenha início.

Leia sobre os impactos e as etapas para sites do Adobe Commerce:

**Adobe Commerce hospedado em nosso produto na nuvem**

Se você estiver usando o Adobe Commerce na infraestrutura em nuvem, trabalhe com sua equipe de tecnologia para reimplantar o Adobe Commerce a qualquer momento\* e aproveitar as vantagens da atualização. Recomendamos que os comerciantes concluam essa redistribuição até 30 de setembro, a fim de evitar problemas de conformidade com o PCI que podem entrar em vigor como resultado dessas vulnerabilidades no final do mês.

Observações adicionais sobre a reimplantação do site na nuvem para esta atualização:

* Se o seu site ainda estiver usando o PHP versão 7.0, você precisará fazer upgrade para uma versão suportada do PHP primeiro antes de reimplantar para aproveitar essas atualizações de segurança.
* Para 2.1.x/2.2.x, mais informações sobre como atualizar o PHP podem ser encontradas [aqui](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html).

\* *As versões anteriores deste artigo e nossas mensagens começaram em 19 de setembro, mas nossas equipes concluíram o trabalho antes do agendamento.*

**Adobe Commerce em todas as outras soluções de hospedagem**

Como o Adobe Commerce depende do PHP, recomendamos que todos os comerciantes que usam o Adobe Commerce analisem as atualizações necessárias para o PHP com seus provedores de hospedagem. Também recomendamos que os comerciantes concluam essa análise e todas as atualizações até 30 de setembro para evitar problemas de conformidade com o PCI que possam ocorrer como resultado dessas vulnerabilidades no final do mês.

Observe alguns detalhes adicionais do Adobe Commerce em outras soluções de hospedagem:

* As versões 2.0 ou 1.x do Adobe Commerce que utilizam versões do PHP anteriores à 7.1 ou posteriores não têm patch oficial do PHP disponível. O caminho recomendado é atualizar o PHP para uma versão suportada do PHP.

De acordo com o alerta, os patches recomendados para essa vulnerabilidade incluem:

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.2](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Se quiser obter mais informações sobre PHP e lançamentos recentes, visite [Site do PHP](https://www.php.net/). E se você tiver dúvidas ou quiser obter mais informações sobre as práticas recomendadas de segurança, consulte nosso [Guia de práticas recomendadas de segurança](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
