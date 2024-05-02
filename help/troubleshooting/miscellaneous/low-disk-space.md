---
title: Pouco espaço em disco
description: Este artigo sugere soluções para a situação em que não há espaço suficiente em determinado ambiente do Adobe Commerce na infraestrutura em nuvem.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Pouco espaço em disco

Este artigo sugere soluções para a situação em que não há espaço suficiente em determinado ambiente do Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, tudo [versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Você está ficando sem espaço em disco com diretórios graváveis. Um sintoma pode ser [implantação paralisada](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Para verificar o uso do disco, execute o seguinte comando:

```bash
df -h var/
```

## Causa

A variável `var` O diretório geralmente é o que pode ocupar muito espaço e pode ser limpo facilmente.

O Adobe Commerce armazena todos os arquivos de log no `var` diretório. Novos arquivos de registro são criados e os antigos são arquivados diariamente. Mas se o número de erros gerados continuar crescendo, os arquivos de log ocupam cada vez mais espaço.

Os arquivos personalizados de importação/exportação também são armazenados no `var` e ocuparão espaço se seus números aumentarem.

## Solução

Opções de solução:

* Verifique se você tem arquivos de log grandes e investigue por que eles são grandes; corrija o problema que gera uma grande quantidade de saída de log.
* Limpe o `var` diretório.
* Configure um trabalho cron para rastrear o tamanho do `var` e limpe-o.
* Aloque mais espaço em disco, se você tiver algum espaço não utilizado. (Consulte a seção abaixo para obter informações sobre como verificar qual é o limite de espaço.)
   * Para os ambientes do plano Starter, todos os ambientes e os ambientes de Integração do plano Pro, é possível alocar o espaço em disco se você tiver algum não utilizado, conforme descrito em [Gerenciar espaço em disco: Alocando espaço em disco](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * Para ambientes de preparo e produção planejados Pro, entre em contato com o suporte para alocar mais espaço em disco se você tiver algum não utilizado.
* Se você tiver atingido o limite de espaço e ainda enfrentar problemas de pouco espaço, considere comprar mais espaço em disco, entre em contato com a equipe de conta do Adobe para obter detalhes.

### Verificar limite de espaço em disco

Para verificar a quantidade de espaço disponível para cada Adobe Commerce no ambiente de infraestrutura em nuvem:

1. Faça logon no [Cloud Console](https://console.adobecommerce.com).
1. No **[!UICONTROL All projects]** selecione o projeto relevante. No canto esquerdo, você verá a disponibilidade de espaço em disco.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
