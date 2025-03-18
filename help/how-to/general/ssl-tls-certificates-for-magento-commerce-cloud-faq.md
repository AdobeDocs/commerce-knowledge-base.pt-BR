---
title: Certificados SSL (TLS) para Adobe Commerce na infraestrutura em nuvem
description: Este artigo fornece respostas rápidas a perguntas sobre como obter certificados SSL (TLS) para o seu site do Adobe Commerce na nossa infraestrutura em nuvem.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 7694e6cb739d73a28c902e95d324b1317f4daaf6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# Certificados SSL (TLS) para Adobe Commerce na infraestrutura em nuvem

Este artigo fornece respostas rápidas a perguntas sobre como obter certificados SSL (TLS) para o seu site do Adobe Commerce na nossa infraestrutura em nuvem.

## Qual certificado SSL/TLS a Adobe fornece?

A Adobe fornece um [Vamos criptografar o certificado SSL/TLS](https://letsencrypt.org/) validado pelo domínio para proteger o tráfego HTTPS de [!DNL Fastly]. O Adobe fornece um certificado para cada ambiente de arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Pro, Preparo e Adobe Commerce na infraestrutura em nuvem Starter para proteger todos os domínios nesse ambiente.

## O que é coberto por um certificado?

Para a arquitetura do plano Pro, os ambientes dedicados de preparo e produção terão um certificado SSL criado. Cada ambiente dedicado fora dos ambientes de Integração da Platform-as-a-Service (PaaS) terá esse certificado para os URLs atribuídos a esse ambiente.

Para os ambientes de arquitetura de plano inicial e Integração PaaS, haverá um domínio técnico padrão provisionado com o ambiente e protegido por um certificado separado.

## Como adicionar um novo domínio para o certificado existente?

Para adicionar o domínio ao serviço em [!DNL Fastly]:

1. Aponte seu domínio no DNS para prod.magentocloud.map.fastly.net e aguarde até 6 horas.
1. [Envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a adição deste domínio na configuração do Nginx (se não tiver feito isso antes).

## Como solicitar um certificado?

Caso 1

Se você ainda não iniciou um site, pode ter recebido o CNAME do Desafio ACME do seu Consultor técnico do cliente (CTA). Você só precisará de um desafio do ACME se não conseguir apontar imediatamente seu DNS para o URL de produção e precisar obter os certificados SSL criados com antecedência.

Caso 2

Se o site já estiver no ar e/ou se você puder apontar os URLs que serão usados para o site no ar imediatamente, não será necessário solicitar um CNAME ACME. Depois de adicionar as URLs conforme necessário ao site da infraestrutura na nuvem do Adobe Commerce e apontar seu DNS para [!DNL Fastly], a validação de HTTP funcionará e criará seu certificado SSL pela primeira vez ou atualizará seu certificado com URLs adicionais.

## Posso usar meu próprio certificado SSL/TLS?

Você pode fornecer seu próprio certificado SSL/TLS em vez de usar o [Vamos criptografar o certificado](https://letsencrypt.org/) fornecido pela Adobe.

No entanto, esse processo requer trabalho adicional para configurar e manter. Primeiro, você precisará gerar uma Solicitação de assinatura de certificado (CSR) para o nome de domínio do site (ou nome comum) e fornecê-la ao fornecedor de SSL para fornecer um certificado SSL.

Depois de ter o certificado SSL, envie um [tíquete de Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ou trabalhe com sua CTA para adicionar certificados hospedados personalizados aos seus ambientes de nuvem.

* Se os domínios não estiverem mais em uso, eles serão automaticamente removidos do nosso sistema e nenhuma outra ação será necessária.
* Se você já possui um certificado, carregue-o usando um cliente SFTP (SSH File Transfer Protocol) para um local de arquivo inacessível pela Web em seu servidor e [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para que eles saibam o caminho do arquivo.

>[!WARNING]
>
>É importante não fazer upload dos arquivos do certificado diretamente no ticket. Caso contrário, os certificados serão considerados comprometidos e a Adobe precisará solicitar um novo certificado.
>Os arquivos devem ser carregados via SFTP no servidor para uma pasta de sua escolha, por exemplo, `var/ssl`, `/tmp/ssl`, etc. - não use outros métodos, como confirmar os arquivos no repositório (o que só deve ser feito para arquivos imutáveis que não contenham dados confidenciais).

## O nome do certificado

O nome do certificado SSL só importa para o URL principal, e é o nome de host principal nomeado pelo primeiro URL e deve corresponder a para ser validado e criado. Se você tiver alguns URLs, eles serão adicionados como entradas de nome alternativo da entidade no certificado. Se você tiver vários URLs apontando para um site do Adobe Commerce na infraestrutura em nuvem, terá apenas uma certificação de URL de nome comum que terá nomes alternativos de assunto anexados para proteger seu site com SSL.

## Que domínio será exibido no campo Nome Comum do certificado?

O domínio exibido no certificado é apenas o primeiro domínio adicionado ao certificado TLS, ele preenche o campo **Nome Comum** (**CN**) e os navegadores exibem esse nome primeiro. O campo **Nome Alternativo da Entidade** (**SAN**) contém todos os nomes DNS para o certificado TLS. Não há como alterar ou solicitar o Nome comum exibido.

## Posso usar certificados TLS curingas?

Certificados TLS curinga só podem ser usados com seu certificado personalizado e não com certificados Let&#39;s Encrypt da Adobe Commerce. Como parte de nossa otimização de TLS, a Adobe está encerrando o suporte a certificados TLS curinga. Estamos identificando e entrando em contato com comerciantes que usam um certificado curinga com certificados Let&#39;s Encrypt da Adobe e estão configurados no console [!DNL Fastly] para o Adobe Commerce. Pedimos que esses certificados curingas sejam substituídos por domínios exatos para garantir a cobertura TLS. Para substituir um certificado TLS curinga, visite a [seção de domínio](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) do plug-in [!DNL Fastly]. Aqui, domínios exatos podem ser adicionados e o curinga pode ser removido. Observe que o DNS precisará apontar para [!DNL Fastly] para que esses novos domínios sejam roteados pela CDN. Depois que os domínios forem adicionados e o DNS for atualizado, um certificado [Let&#39;s Encrypt](https://letsencrypt.org/) correspondente será provisionado. Se você não remover um domínio que aponte para [!DNL Fastly] usando um curinga, o Adobe excluirá o certificado compartilhado. Isso pode resultar em uma interrupção do site se você não tiver o FQDN de URL configurado e o mesmo FQDN de URL configurado em seu DNS. Portanto, você deve confirmar se as URLs configuradas também têm uma correspondência um para um no DNS que aponta para [!DNL Fastly].

## O que devo fazer se meu domínio não estiver mais apontando para o Adobe Commerce?

Se o seu domínio não estiver mais apontando para o Adobe Commerce, remova-o do sistema [!DNL Fastly]/Adobe Commerce. Consulte [!DNL Fastly] [Excluindo um domínio](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) para saber mais. Embora não seja necessário apontar seu domínio para a Adobe Commerce, confirme se é necessário um certificado TLS de domínio de nível superior. Se um domínio de nível superior for necessário, atualize o DNS para apontar para a Adobe Commerce. Se ele já estiver apontando para o Adobe Commerce, atualize seu registro CAA para incluir [lets-encrypt](https://letsencrypt.org/). Se executar essas etapas, você verá o certificado LE atualizado com os URLs secundários necessários que o certificado cobre.&#x200B;

## Leitura relacionada

[Provisionar certificados SSL/TLS](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) na documentação do desenvolvedor
