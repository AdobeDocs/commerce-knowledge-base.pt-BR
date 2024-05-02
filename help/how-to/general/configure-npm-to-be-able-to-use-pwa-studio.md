---
title: Configurar NPM para poder usar o PWA Studio
description: '''[Aplicativos Web progressivos (PWA) Studio](https://magento.github.io/pwa-studio/) é um novo projeto disponível para o Adobe Commerce na infraestrutura em nuvem 2.3.x ou posterior. Para usar e instalar o PWA Studio, é necessário definir a versão do gerenciador de pacotes NPM como 5.x ou posterior para obter suporte para Node.js 8.x. Isso é feito na seção "hooks:build" do arquivo de configuração ".magento.app.yaml".'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Configurar NPM para poder usar o PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) O é um novo projeto disponível para o Adobe Commerce na infraestrutura em nuvem 2.3.x ou posterior. Para usar e instalar o PWA Studio, é necessário definir a versão do gerenciador de pacotes NPM como 5.x ou posterior para obter suporte para Node.js 8.x. Isso é feito no `hooks:build` seção do `.magento.app.yaml` arquivo de configuração.

## Ambiente e tecnologias

* Adobe Commerce na infraestrutura em nuvem 2.3.X
* PWA para Adobe Commerce

## Definir versão do NPM: etapas

Para definir a versão NPM necessária, especifique-a na caixa `.magento.app.yaml` arquivo de configuração. Siga estas etapas:

1. No ambiente de desenvolvimento local, localize o `.magento.app.yaml` arquivo de configuração.
1. Abra o arquivo para edição usando o editor de texto simples ou o IDE.
1. Defina a versão necessária no `hooks:build` seção. No exemplo a seguir, a configuração está definida para instalar o NPM v9.5.0, o mais alto disponível no momento (4 de fevereiro de 2019):

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Se você quiser executar Node.JS em seu aplicativo e não apenas em sua build, adicione os seguintes comandos para alterar seu gancho de build:
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Salvar alterações no arquivo.
1. O Git envia o arquivo editado para o seu [ambiente de integração](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

As alterações entrarão em vigor depois que o Git enviar o arquivo YAML atualizado para o ambiente.

## Documentação relacionada

* [Configuração do aplicativo: ganchos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html) em nosso Guia de infraestrutura do Adobe Commerce na nuvem.
