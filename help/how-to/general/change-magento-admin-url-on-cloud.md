---
title: Alterar o URL do administrador no Adobe Commerce na infraestrutura em nuvem
description: Por padrão, o URL do [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) é definido como *&lt;domain\_name&gt;/admin*. Este artigo mostra como alterar o URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Alterar o URL do administrador no Adobe Commerce na infraestrutura em nuvem

Por padrão, a variável [Administrador do Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) O URL está definido como *&lt;domain _name=&quot;&quot;>/admin*. Este artigo mostra como alterar o URL.

## Método 1: alterar usando o Administrador

Leia as etapas: [Usar um URL de administração personalizado > Alterar do administrador](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) em nosso guia do usuário.

## Método 2: adicionar variável de ambiente ADMIN\_URL

### Ambiente de integração

No [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), adicione uma nova variável com:

**Nome:** ADMIN\_URL **Valor:** novo URL de administração

* Para obter etapas detalhadas, consulte [adicionar variáveis de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) na documentação do desenvolvedor.
* Consulte também [variáveis de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) na documentação do desenvolvedor.

### Quando o Preparo e a Produção não estão disponíveis no Cloud Console

[Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a adição da variável ADMIN\_URL para o ambiente de preparo ou produção.

Se o Preparo e a Produção puderem ser acessados no Cloud Console, adicione a Variável de ambiente conforme descrito na seção *Ambiente de integração* acima.

### Adicionar variáveis usando a CLI da nuvem

Você pode adicionar a variável ADMIN\_URL usando o seguinte comando da CLI da nuvem (para principal):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Para obter instruções mais detalhadas, consulte [Alterar o URL do administrador](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) no tópico Variáveis de administração no Guia de infraestrutura do Commerce na nuvem.

Observe que o uso da CLI da nuvem para alterar a variável ADMIN\_URL aciona uma reimplantação do ambiente. As variáveis são herdáveis por padrão; para impedir a herança, use as opções de comando da CLI da nuvem para indicar que você não deseja que o valor da variável seja herdado por ambientes secundários. Consulte a [Visibilidade](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) tópico em Níveis variáveis no Guia de infraestrutura do Commerce na nuvem.
