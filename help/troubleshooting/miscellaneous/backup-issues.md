---
title: Problemas de backup
description: Este artigo lista as possíveis soluções para os problemas de criação de backup.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Problemas de backup

Este artigo lista as possíveis soluções para os problemas de criação de backup.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.x
* Magento Open Source 2.3.x

## Backup desabilitado {#backup-disabled}

Se a funcionalidade de backup do Adobe Commerce não iniciar ou exibir a seguinte mensagem, será necessário ativar o recurso antes de fazer o backup.

```terminal
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Digite o seguinte comando da CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Para obter informações adicionais sobre backups, consulte [Fazer backup e reverter o sistema de arquivos, a mídia e o banco de dados.](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## Espaço em disco insuficiente {#insufficient-disk-space-trouble-backup-space-}

Se o backup falhar devido a espaço em disco insuficiente, você deverá liberar espaço em disco movendo alguns arquivos para outro dispositivo de armazenamento ou unidade. No entanto, pode haver outras maneiras de resolver o problema. Consulte um dos seguintes recursos para obter dicas:

* [8 Dicas para Resolver Problemas de Disco Rígido dos Sistemas Linux e Unix, como Disco Cheio ou Não Pode Gravar no Disco](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfault: df diz que o disco está cheio, mas não está](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: controlando para onde o espaço em disco foi no Linux?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Erro do sistema operacional {#operating-system-error-trouble-backup-os-}

Infelizmente, não podemos recomendar nada específico devido à variedade de erros que você pode encontrar. Entretanto, podemos sugerir que você:

* Entre em contato com o administrador do sistema.
* Pesquisar fóruns públicos como [Stack Exchange](https://unix.stackexchange.com) ou [Stack Overflow](https://stackoverflow.com)
* Abra um [problema do GitHub](https://github.com/magento/magento2/issues) e tentaremos ajudar.

## Falha no backup {#backup-fails-trouble-backup-all-}

Se o backup falhar ou se todos os testes de backup falharem, é possível que o [proprietário do sistema de arquivos do Adobe Commerce](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) não tenha privilégios suficientes e propriedade do sistema de arquivos do Adobe Commerce. Por exemplo, outro usuário pode ser o proprietário dos arquivos ou os arquivos podem ser somente leitura.

Preste atenção especial às permissões do sistema de arquivos e à propriedade do diretório e dos subdiretórios `<magento_root>/var`. Para obter mais informações, consulte [Definir permissões e propriedade do sistema de arquivos](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
