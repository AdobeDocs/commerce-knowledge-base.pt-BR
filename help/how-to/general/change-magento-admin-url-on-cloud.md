---
title: Alterar o URL do administrador no Adobe Commerce na infraestrutura em nuvem
description: Por padrão, o URL do [Commerce Admin](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/start/admin/admin) é definido como *&lt;domain_name&gt;/admin*. Este artigo mostra como alterar o URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Alterar o URL do administrador no Adobe Commerce na infraestrutura em nuvem

Por padrão, a URL do [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html?lang=pt-BR) está definida como *&lt;domain\_name>/admin*. Este artigo mostra como alterar o URL.

## Método 1: alterar usando o Administrador

Leia as etapas: [Usando um URL de Administração Personalizado > Alterar do Administrador](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=pt-BR#use-a-custom-admin-url) em nosso guia do usuário.

## Método 2: adicionar variável de ambiente ADMIN\_URL

### Ambiente de integração

No [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=pt-BR), adicione uma nova variável com:

**Nome:** ADMIN\_URL **Valor:** URL do novo Administrador

* Para obter etapas detalhadas, consulte [adicionar variáveis de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=pt-BR#configure-environment) na documentação do desenvolvedor.
* Consulte também [variáveis de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=pt-BR) em nossa documentação para desenvolvedores.

### Quando o Preparo e a Produção não estão disponíveis no Cloud Console

[Envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a adição da variável ADMIN\_URL para o ambiente de preparo ou produção.

Se o Preparo e a Produção puderem ser acessados pelo Console da Nuvem, adicione a Variável de Ambiente conforme descrito na seção *Ambiente de integração* acima.

### Adicionar variáveis usando a CLI da nuvem

Você pode adicionar a variável ADMIN\_URL usando o seguinte comando da CLI da nuvem (para principal):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Para obter instruções mais detalhadas, consulte [Alterar o URL do Administrador](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=pt-BR#change-the-admin-url) no tópico Variáveis de administração no Guia de Infraestrutura do Commerce na Nuvem.

Observe que o uso da CLI da nuvem para alterar a variável ADMIN\_URL aciona uma reimplantação do ambiente. As variáveis são herdáveis por padrão; para impedir a herança, use as opções de comando da CLI da nuvem para indicar que você não deseja que o valor da variável seja herdado por ambientes secundários. Consulte o tópico [Visibilidade](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=pt-BR#visibility) em Níveis de variáveis no Guia de Infraestrutura do Commerce na Nuvem.
