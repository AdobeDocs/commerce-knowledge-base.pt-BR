---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Guia de validação de metadados

Para garantir a formatação correta dos metadados em arquivos MD, implementamos um teste de validação de metadados. Este documento fornece diretrizes para ajudar os colaboradores a evitar alguns dos erros mais comuns de validação de metadados.

**Exemplo de metadados:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Erros comuns de validação e como evitá-los/corrigi-los

Veja a seguir alguns dos cenários mais comuns em que ocorrem erros de validação de metadados.

### Dois pontos nos metadados

Um erro de validação ocorrerá se o título ou os rótulos, ou ambos, tiverem dois pontos.

**Exemplo:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

Para evitar esse erro, envolva o título ou os rótulos (ou ambos se tiverem dois pontos) em **aspas simples**.

**Exemplo:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Dois pontos e aspas simples ou apóstrofe nos metadados

A solução anterior não funcionará se houver dois pontos, aspas simples ou apóstrofos no título ou nos rótulos.

**Exemplo:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Este erro é corrigido ao envolver o título ou os rótulos (ou ambos) em **aspa dupla**.

**Exemplo:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Dois-pontos, aspas duplas e aspas simples ou apóstrofe nos metadados

**Exemplo:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

Quando isso acontecer, envolva o título ou os rótulos (ou ambos) em **aspa dupla** e usar um **barra invertida** para evitar todas as aspas duplas no título e nos rótulos.

**Exemplo:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Campos ausentes nos metadados

Um erro de validação ocorrerá se o campo de título ou o campo de rótulos estiver ausente nos metadados.

**Exemplo:**

```markdown
---
title: This is a title
---
```

OU

```markdown
---
labels: article,labels,tags
---
```

Para evitar esse erro, inclua ambos os campos nos metadados.

O campo de rótulos pode ficar vazio e não resultará em erro, mas o campo de título deve ser preenchido.

**Exemplo:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
