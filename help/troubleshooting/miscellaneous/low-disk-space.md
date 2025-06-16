---
title: Pouco espaço em disco
description: Este artigo sugere soluções para a situação em que não há espaço suficiente em determinado ambiente do Adobe Commerce na infraestrutura em nuvem.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Pouco espaço em disco

Este artigo sugere soluções para a situação em que não há espaço suficiente em determinado ambiente do Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Você está ficando sem espaço em disco com diretórios graváveis. Um sintoma pode ser [implantação paralisada](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26878).

Para verificar o uso do disco, execute o seguinte comando:

```bash
df -h var/
```

## Causa

O diretório `var` geralmente é aquele que pode ocupar muito espaço e pode ser limpo facilmente.

O Adobe Commerce armazena todos os arquivos de log no diretório `var`. Novos arquivos de registro são criados e os antigos são arquivados diariamente. Mas se o número de erros gerados continuar crescendo, os arquivos de log ocupam cada vez mais espaço.

Os arquivos personalizados de importação/exportação também são armazenados no diretório `var` e ocupam espaço se seus números aumentarem.

## Solução

Opções de solução:

* Verifique se você tem arquivos de log grandes e investigue por que eles são grandes; corrija o problema que gera uma grande quantidade de saída de log.
* Limpe o diretório `var`.
* Configure um trabalho cron para rastrear o tamanho do diretório `var` e limpá-lo.
* Aloque mais espaço em disco, se você tiver algum espaço não utilizado. (Consulte a seção abaixo para obter informações sobre como verificar qual é o limite de espaço.)
   * Para os ambientes de plano Starter, todos os ambientes e Integração de plano Pro, é possível alocar o espaço em disco se você tiver algum espaço não utilizado, conforme descrito em [Gerenciar espaço em disco: Alocando espaço em disco](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space).
   * Para ambientes de preparo e produção planejados Pro, entre em contato com o suporte para alocar mais espaço em disco se você tiver algum não utilizado.
* Se você tiver atingido o limite de espaço e ainda enfrentar problemas de pouco espaço, considere comprar mais espaço em disco, entre em contato com a equipe de conta da Adobe para obter detalhes.

### Verificar limite de espaço em disco

Para verificar a quantidade de espaço disponível para cada Adobe Commerce no ambiente de infraestrutura em nuvem:

1. Faça logon no [Cloud Console](https://console.adobecommerce.com).
1. No painel **[!UICONTROL All projects]**, selecione o projeto relevante. No canto esquerdo, você verá a disponibilidade de espaço em disco.

   ![espaço_projeto.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
