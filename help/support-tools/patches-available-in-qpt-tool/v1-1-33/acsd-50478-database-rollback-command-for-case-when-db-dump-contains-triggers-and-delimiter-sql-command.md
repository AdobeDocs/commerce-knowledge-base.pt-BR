---
title: "ACSD-50478: Problema de JS para ação de reversão na grade de backups e no comando de reversão do banco de dados"
description: Aplique o patch ACSD-50478 para corrigir o problema de JS para a ação de reversão na grade de backups e o comando de reversão do banco de dados para um caso em que o despejo do banco de dados contém acionadores e um comando SQL *delimitador*.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478: Problema de JS para ação de reversão na grade de backups e comando de reversão do banco de dados

O patch ACSD-50478 corrige o problema de JS para a ação de reversão na grade de backups e o comando de reversão do banco de dados para um caso em que o despejo de banco de dados contém acionadores e um *delimitador* Comando SQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.33 está instalado. A ID do patch é ACSD-50478. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problema de JS para a ação de reversão na grade Backups e o comando de reversão do banco de dados para um caso em que o despejo de banco de dados contém acionadores e um *delimitador* Comando SQL.

<u>Etapas a serem reproduzidas</u>:

1. Definir indexadores como [!UICONTROL Update on Schedule] para que os acionadores sejam criados no banco de dados.
1. Habilite a funcionalidade de backup na linha de comando:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Ir para **Sistema** > **Ferramentas** > **Backups** e gerar um backup de BD.
1. Abra o console do navegador; você verá o seguinte erro:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Tente importar o BD da linha de comando:

   `bin/magento setup:rollback --db-file="<filename>"`

1. O seguinte erro é exibido:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Resultados esperados</u>:

A restauração do banco de dados é bem-sucedida a partir do Admin e da linha de comando.

<u>Resultados reais</u>:

Você observou os erros mencionados nas etapas 4 e 6.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
