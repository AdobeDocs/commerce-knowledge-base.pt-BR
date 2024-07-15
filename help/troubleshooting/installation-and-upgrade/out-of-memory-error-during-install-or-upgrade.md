---
title: Erro de falta de memória durante a instalação ou atualização
description: Este artigo fala sobre soluções para o erro de falta de memória durante a instalação/atualização de produtos Adobe Commerce no local e Magento Open Source no local.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Erro de falta de memória durante a instalação ou atualização

Este artigo fala sobre soluções para o erro de falta de memória durante a instalação/atualização de produtos Adobe Commerce no local e Magento Open Source no local.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.x
* Magento Open Source no local 2.3.x

## Problema

Ao instalar ou atualizar o aplicativo Adobe Commerce ou Magento Open Source ou componentes como extensões, temas ou pacotes de idiomas, usando o Assistente de configuração da Web, um erro semelhante ao seguinte é exibido:

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

O erro

```bash
proc_open(): fork failed - Cannot allocate memory
```

O também pode ser exibido na linha de comando.

## Solução {#solution}

Recomendamos que você [aloque 2GB de memória para o PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) em nossa documentação do desenvolvedor para ter certeza de que sua instalação ou atualização terá êxito.

Se você já tiver feito isso, crie um arquivo de troca em sua máquina. Um computador Linux usa *espaço de troca* se precisar de mais recursos de memória e a RAM estiver cheia. O espaço de permuta é usado para páginas inativas na memória.

Estas são apenas sugestões; outras opções podem estar disponíveis. Consulte um administrador de rede ou outro recurso qualificado antes de continuar. Você deve executar os comandos para criar um arquivo de troca como um usuário com privilégios `root`.

### Trocar arquivo no Ubuntu {#swap-file-on-ubuntu}

Use o comando `fallocate` conforme discutido nestas referências:

* [Como adicionar troca no Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Como Adicionar Espaço De Troca No Ubuntu 16.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [PerguntasFrequentesSwap (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Trocar arquivo no CentOS {#swap-file-on-centos}

Use o comando `mkswap` conforme discutido nestas referências:

* [Como Adicionar Troca no CentOS 6 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Como Adicionar Troca no CentOS 7 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Espaço de Troca (portal do cliente RedHat)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
