---
title: Durante a instalação, o aviso de data do PHP
description: Este artigo fornece uma correção para um aviso de data PHP durante a instalação.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Durante a instalação, o aviso de data do PHP

Este artigo fornece uma correção para um aviso de data PHP durante a instalação.

## Detalhes {#details}

Durante a instalação, a seguinte mensagem é exibida:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Solução {#solution}

Verifique cuidadosamente a configuração do fuso horário do PHP. Consulte [Guia de Instalação > Configurações do PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) na documentação do desenvolvedor.
