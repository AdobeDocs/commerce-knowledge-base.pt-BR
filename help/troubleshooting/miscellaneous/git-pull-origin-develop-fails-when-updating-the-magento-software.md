---
title: o desenvolvimento da origem de pull do git falha ao atualizar o software Adobe Commerce
description: Este artigo fornece uma correção para quando não é possível atualizar o software Adobe Commerce ao executar "git pull origin develop".
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%
---
# o desenvolvimento da origem de pull do git falha ao atualizar o software Adobe Commerce

Este artigo fornece uma correção para quando não é possível atualizar o software Adobe Commerce ao executar `git pull origin develop`.

## Detalhes

Uma das etapas para atualizar o software Adobe Commerce é atualizar o repositório local executando:

```bash
$ git pull origin develop
```

O seguinte erro pode ser exibido:

```bash
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Para descobrir quais arquivos estão sujeitos a serem sobregravados, leia a mensagem ou digite:

```bash
git status
```

A próxima seção discute soluções sugeridas.

### Soluções sugeridas

Sua solução depende de você ter ou não modificado intencionalmente os arquivos no sistema de arquivos do Adobe Commerce. Consulte uma das seções a seguir para obter mais informações.

#### Você modificou arquivos intencionalmente

Resolva manualmente os conflitos da maneira usual. Se não tiver certeza do que fazer, consulte a [ajuda do GitHub](https://help.github.com/).

#### Você não modificou nenhum arquivo intencionalmente

Tente qualquer um dos seguintes procedimentos:

* Se você tiver certeza de que não modificou nenhum arquivo e não se importa com a remoção ou substituição das alterações no sistema de arquivos do Adobe Commerce, digite:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Depois disso, continue de onde parou com a atualização do Adobe Commerce.

* É possível que uma configuração do GitHub possa evitar esses erros no futuro. Por padrão, o GitHub armazena conteúdo usando os caracteres de fim de linha padrão do sistema operacional. Se você estiver usando o Linux, mas outro colaborador tiver feito uma alteração usando o Windows, o GitHub converte os finais de linha do Windows para Linux quando você clona ou obtém. Isso dá a aparência de uma alteração nos arquivos quando, na verdade, nenhuma alteração foi feita.

  Para configurar o GitHub para ignorar terminações de linha, insira o seguinte comando no cliente Git:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Se você usa o Windows, digite:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >A Adobe não recomenda ou endossa nenhuma configuração específica do GitHub. As anteriores são apenas sugestões. Para obter mais informações, consulte a [ajuda do GitHub](https://help.github.com/).

  Continue de onde parou com a atualização do Adobe Commerce.
