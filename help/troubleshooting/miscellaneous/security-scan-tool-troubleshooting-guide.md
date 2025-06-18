---
title: Guia de solução de problemas da ferramenta Adobe Commerce Security Scan
description: Saiba como solucionar os vários problemas com a ferramenta Security Scan for Adobe Commerce e Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: c6e338fb33477ab107fe4de382b485339b57275a
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Guia de solução de problemas da ferramenta Adobe Commerce Security Scan

Saiba como solucionar os vários problemas com a ferramenta Security Scan for Adobe Commerce e Magento Open Source.

## Problema: não é possível enviar o site

A ferramenta Verificação de segurança exige que você comprove a propriedade do site antes que o domínio possa ser adicionado à Ferramenta de verificação de segurança. Isso pode ser feito adicionando um código de confirmação ao site usando um comentário do HTML ou a tag `<meta>`. O comentário HTML deve ser colocado dentro da tag `<body>`, por exemplo, na seção de rodapé. A tag `<meta>` deve ser colocada dentro da seção `<head>` da página.

Um problema comum enfrentado pelos comerciantes ocorre quando a Ferramenta de verificação de segurança não consegue confirmar a propriedade do site do comerciante.

Se você estiver recebendo um erro e não puder enviar seu site para verificação, consulte o artigo [Mensagem de erro ao adicionar sites à Verificação de Segurança](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) na nossa base de dados de suporte.

## Problema: Relatórios vazios gerados pela ferramenta Verificação de segurança

Você obtém relatórios de verificação vazios da ferramenta Verificação de Segurança ou obtém relatórios contendo apenas um erro, como *A ferramenta de segurança não conseguiu acessar a URL base* ou a instalação do *Magento não foi encontrada na URL fornecida*.

### Solução

1. Verifique se os IPs do 52.87.98.44, 34.196.167.176 e 3.218.25.102 não estão bloqueados nas portas 80 e 443.
1. Verifique se há redirecionamentos na URL enviada (por exemplo, `https://mystore.com` redireciona para `https://www.mystore.com` ou vice-versa ou redireciona para outros nomes de domínio).
1. Investigue os logs de acesso do servidor da WAF/Web para solicitações rejeitadas/não atendidas. HTTP 403 `Forbidden` e HTTP 500 `Internal server error` são as respostas comuns do servidor que causam geração de relatórios vazios. Este é um exemplo do código de confirmação que bloqueia solicitações por agentes do usuário:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Você também pode ver o artigo [O relatório da Ferramenta de verificação de segurança está em branco](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) em nossa base de dados de conhecimento de suporte para obter mais informações.

## Problema: Problema de segurança resolvido, mas ainda sendo exibido como vulnerável na verificação

Você resolveu um problema de segurança e espera que a Verificação de segurança mostre que não está mais vulnerável ao problema recém-resolvido. Em vez disso, você descobrirá que o relatório gerado pela Verificação de segurança ainda o relata como vulnerável ao problema de segurança.

### Causa

Os metadados da instância da nuvem são coletados apenas para `active` e `live` Projetos na nuvem e NÃO é um processo em tempo real.

O script de coleta de estatísticas é executado uma vez por dia e, em seguida, a ferramenta Security Scan (Verificação de segurança) precisa coletar os novos dados posteriormente.

A latência esperada do ciclo de sincronização é de até uma semana e leva no mínimo 24 horas.

Os seguintes status podem aparecer nas verificações:

1. **Aprovado**: a ferramenta Verificação de Segurança verificou os dados atualizados e aprovou as alterações.
1. **Desconhecido**: a ferramenta Verificação de Segurança ainda não tem dados sobre seu domínio; aguarde o próximo ciclo de sincronização.
1. **Falha**: se o status mostrar falha, você precisará corrigir o problema (habilitar 2FA, alterar URL do administrador, etc.) e aguardar o próximo ciclo de sincronização.

Se 24 horas tiverem se passado desde que as alterações foram feitas na instância e elas não forem refletidas no relatório de Verificação de Segurança, você poderá [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Forneça o URL da loja ao enviar o tíquete.

## Falha de suspeita de BotNet

Você recebe uma notificação sobre a falha &quot;BotNet Suspect&quot;.

### Causa

1. O nome de domínio da loja entrou em uma &quot;Lista de participantes potenciais do BotNet&quot; em 2019, e teve o painel de administração, o downloader ou a funcionalidade de RSS expostos publicamente, e/ou seu URL foi mencionado nos fóruns de desativação do CC.
1. O alerta pode ser causado por sinais de comprometimento da loja e/ou malware, como o JavaScript encontrado na página.
1. Não é necessariamente um problema em andamento. Se a loja tiver sido comprometida anteriormente, seu nome de host ainda poderá flutuar pela Internet escura como um nome de &quot;vítima&quot;.
1. Isso também pode ser causado não pelo Adobe Commerce, mas por um comprometimento do sistema (no nível do SO).

### Solução

1. Verifique as contas SSH recém-criadas, as alterações no sistema de arquivos etc.
1. Execute uma revisão de segurança.
1. Verifique a versão e a atualização do Adobe Commerce, especialmente se ele ainda estiver executando o Magento 1, que não é mais compatível.
1. Se o problema persistir, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e forneça a URL de armazenamento.

## Problema: Falha na injeção de comprometimento

Você recebe um erro em relação a uma falha de &quot;injeção de comprometimento&quot;.

### Solução

1. Revise os scripts indicados no relatório da ferramenta Verificação de segurança.
1. Revise o corpo de origem da página inicial para injeções de script em linha.
1. Executar revisão de alterações de configuração do sistema, especialmente as `HTML head` e `Miscellaneous HTML` personalizadas nos valores de seção `footer`.
1. Executar análise de código e banco de dados para detectar alterações e sinais desconhecidos de malware injetado.

Se nenhuma das situações acima ajudar, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e forneça a URL de armazenamento e a mensagem de erro do relatório.

## Perguntas frequentes

### A Verificação de segurança afetará o desempenho do meu site?

Não. A Verificação de segurança faz todas as solicitações uma por uma como se fossem de um único usuário. Por esse motivo, a Verificação de segurança não deve afetar o desempenho do site.

### Por quanto tempo o Adobe Commerce mantém relatórios do Security Scan?

Você pode gerar os 10 relatórios anteriores no seu lado. Se forem necessários relatórios mais antigos, entre em contato com o suporte da Adobe Commerce.

### Quais informações são necessárias ao enviar um tíquete de suporte?

Forneça o nome de domínio exatamente como foi enviado para a [verificação de segurança](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-26357), MAGEID e Cloud Project_ID. Observe que a Cloud Project_ID não é necessária para o Adobe Commerce no local.

### O que acontece se eu remover minha loja da verificação da ferramenta de verificação?

Se você excluir o envio do armazenamento - todos os dados relacionados, incluindo relatórios de verificação, serão excluídos. Esta operação é irreversível. O envio do domínio de armazenamento após sua exclusão cria um NOVO envio.
