---
title: Guia de solução de problemas da ferramenta Adobe Commerce Security Scan
description: Saiba como solucionar vários problemas com a ferramenta Security Scan for Adobe Commerce e Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Guia de solução de problemas da ferramenta Adobe Commerce Security Scan

Saiba como solucionar vários problemas com a ferramenta Security Scan for Adobe Commerce e Magento Open Source.

## Problema: não é possível enviar o site

A ferramenta Verificação de segurança exige que você comprove a propriedade do site antes que o domínio possa ser adicionado à Ferramenta de verificação de segurança. Isso pode ser feito adicionando um código de confirmação ao site usando um comentário HTML ou o `<meta>` tag. O comentário HTML deve ser colocado dentro do `<body>` tag, por exemplo, na seção do rodapé. A variável `<meta>` deve ser colocada dentro da tag da página `<head>` seção.

Um problema comum enfrentado pelos comerciantes ocorre quando a Ferramenta de verificação de segurança não consegue confirmar a propriedade do site do comerciante.

Se você estiver recebendo um erro e não puder enviar seu site para a verificação, consulte o [Mensagem de erro ao adicionar sites à Verificação de segurança](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) artigo de solução de problemas em nossa base de conhecimento de suporte.

## Problema: Relatórios vazios gerados pela ferramenta Verificação de segurança

Você obtém relatórios de varredura vazios na ferramenta Varredura de segurança ou obtém relatórios contendo apenas um erro, como *A ferramenta de segurança não conseguiu acessar o URL de base* ou *A instalação do Magento não foi encontrada no URL fornecido*.

### Solução

1. Verifique se os IPs 52.87.98.44, 34.196.167.176 e 3.218.25.102 não estão bloqueados nas portas 80 e 443.
1. Verifique se há redirecionamentos no URL enviado (por exemplo, `https://mystore.com` redireciona para `https://www.mystore.com` ou vice-versa ou redireciona para outros nomes de domínio).
1. Investigue os logs de acesso do servidor Web/WAF para solicitações rejeitadas/não atendidas. HTTP 403 `Forbidden` e HTTP 500 `Internal server error` são as respostas comuns do servidor que causam a geração de relatórios vazios. Este é um exemplo do código de confirmação que bloqueia solicitações por agentes do usuário:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Você também pode ver [O relatório da Ferramenta de verificação de segurança está em branco](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) artigo em nossa base de conhecimento de suporte para obter mais informações.

## Problema: Problema de segurança resolvido, mas ainda sendo exibido como vulnerável na verificação

Você resolveu um problema de segurança e espera que a Verificação de segurança mostre que não está mais vulnerável ao problema recém-resolvido. Em vez disso, você descobrirá que o relatório gerado pela Verificação de segurança ainda o relata como vulnerável ao problema de segurança.

### Causa

Os metadados da instância da nuvem são coletados somente para `active` e `live` A nuvem projeta e NÃO é um processo em tempo real.

O script de coleta de estatísticas é executado uma vez por dia e, em seguida, a ferramenta Security Scan (Verificação de segurança) precisa coletar os novos dados posteriormente.

A latência esperada do ciclo de sincronização é de até uma semana e leva no mínimo 24 horas.

Os seguintes status podem aparecer nas verificações:

1. **Aprovado**: A ferramenta Verificação de segurança verificou os dados atualizados e aprovou as alterações.
1. **Desconhecido**: a ferramenta Verificação de segurança ainda não tem dados sobre seu domínio; aguarde o próximo ciclo de sincronização.
1. **Falha**: se o status mostrar falha, você precisará corrigir o problema (habilitar 2FA, alterar URL do administrador etc.) e aguarde o próximo ciclo de sincronização.

Se tiverem decorrido 24 horas desde que as alterações foram feitas na instância e não forem refletidas no relatório de Verificação de segurança, você poderá [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Forneça o URL da loja ao enviar o tíquete.

## Falha de suspeita de BotNet

Você recebe uma notificação sobre a falha &quot;BotNet Suspect&quot;.

### Causa

1. O nome de domínio da loja entrou em uma &quot;Lista de participantes potenciais do BotNet&quot; em 2019, e teve o painel de administração, o downloader ou a funcionalidade de RSS expostos publicamente, e/ou seu URL foi mencionado nos fóruns de desativação do CC.
1. O alerta pode ser causado pelos sinais de comprometimento da loja e/ou malware, como JavaScript encontrado na página.
1. Não é necessariamente um problema em andamento. Se a loja tiver sido comprometida anteriormente, seu nome de host ainda poderá flutuar pela Internet escura como um nome de &quot;vítima&quot;.
1. Isso também pode ser causado não pelo Adobe Commerce, mas por um comprometimento do sistema (no nível do SO).

### Solução

1. Verifique as contas SSH recém-criadas, as alterações no sistema de arquivos etc.
1. Execute uma revisão de segurança.
1. Verifique a versão e a atualização do Adobe Commerce, especialmente se ainda estiver executando o Magento 1, que não é mais compatível.
1. Se o problema persistir, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e forneça o URL da loja.

## Problema: Falha na injeção de comprometimento

Você recebe um erro em relação a uma falha de &quot;injeção de comprometimento&quot;.

### Solução

1. Revise os scripts indicados no relatório da ferramenta Verificação de segurança.
1. Revise o corpo de origem da página inicial para injeções de script em linha.
1. Realizar a revisão das alterações de configuração do sistema, especialmente as personalizadas `HTML head` e `Miscellaneous HTML` in `footer` valores da seção.
1. Executar análise de código e banco de dados para detectar alterações e sinais desconhecidos de malware injetado.

Se nenhuma das situações acima ajudar, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e fornecer o URL de armazenamento e a mensagem de erro do relatório.

## Perguntas frequentes

### A Verificação de segurança afetará o desempenho do meu site?

Não. A Verificação de segurança faz todas as solicitações uma por uma como se fossem de um único usuário. Por esse motivo, a Verificação de segurança não deve afetar o desempenho do site.

### Por quanto tempo o Adobe Commerce mantém relatórios do Security Scan?

Você pode gerar os 10 relatórios anteriores no seu lado. Se forem necessários relatórios mais antigos, entre em contato com o suporte da Adobe Commerce. É possível obter até um ano de relatórios de verificações de segurança anteriores.

### Quais informações são necessárias ao enviar um tíquete de suporte?

Forneça o nome de domínio.
