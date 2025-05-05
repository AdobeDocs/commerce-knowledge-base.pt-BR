---
title: Como adicionar um novo país ao Adobe Commerce
description: Este artigo explica como adicionar um país que não está presente no Adobe Commerce e na Biblioteca local Zend. Isso requer alterações de código e banco de dados que constituem Personalizações do cliente de acordo com os termos aplicáveis do contrato. Observe que os materiais de exemplo incluídos neste artigo são fornecidos "NO ESTADO EM QUE SE ENCONTRAM", sem qualquer garantia. Nem a Adobe nem qualquer entidade afiliada é obrigada a manter, corrigir, atualizar, alterar, modificar ou dar suporte a esses materiais. Aqui vamos descrever os princípios básicos do que precisa ser feito para conseguir isso.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Como adicionar um novo país ao Adobe Commerce

Este artigo explica como adicionar um país que não está presente no Adobe Commerce e na Biblioteca local Zend. Isso requer alterações de código e banco de dados que constituem Personalizações do cliente de acordo com os termos aplicáveis do contrato. Observe que os materiais de exemplo incluídos neste artigo são fornecidos &quot;NO ESTADO EM QUE SE ENCONTRAM&quot;, sem qualquer garantia. Nem a Adobe nem qualquer entidade afiliada é obrigada a manter, corrigir, atualizar, alterar, modificar ou dar suporte a esses materiais. Aqui vamos descrever os princípios básicos do que precisa ser feito para conseguir isso.

Neste exemplo, criamos um novo módulo do Adobe Commerce com um patch de dados que é aplicado na instalação do Adobe Commerce ou no processo de atualização e adicionamos um País abstrato com o código de país XX ao Adobe Commerce. O [Adobe Commerce Diretory](https://developer.adobe.com/commerce/php/module-reference/module-directory/) cria uma lista inicial de países e, em seguida, usa Patches de Configuração para anexar territórios a essa lista. Este artigo explica como criar um novo módulo que anexará um novo país à lista. Você pode revisar o código do módulo existente do Adobe Commerce Diretory para referência. Isso ocorre porque o seguinte módulo de exemplo continua o trabalho do módulo Diretório de criação de uma lista de países e regiões e reutiliza partes do código dos Patches de Configuração do módulo Adobe Commerce Diretory.

## Documentação recomendada

Você deve estar familiarizado com o desenvolvimento do módulo Adobe Commerce para criar um novo.

Consulte os seguintes tópicos em nossa documentação do desenvolvedor antes de tentar criar um novo módulo:

* [Guia do desenvolvedor do PHP](https://developer.adobe.com/commerce/php/development/)
* [Visão geral do módulo](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Criar um Novo Módulo](https://experienceleague.adobe.com/pt-br/docs/commerce-learn/tutorials/backend-development/create-module)
* [Arquivos de configuração de módulo](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/files/module-files)

## Informações necessárias

Um novo país deve ter um nome exclusivo, ID do país, ISO2 e códigos ISO3 em toda a Adobe Commerce.

## Estrutura do módulo

Neste exemplo, vamos criar um novo módulo chamado \`ExtraCountry\` com a seguinte estrutura de diretório:

(Para saber mais sobre a estrutura do módulo, consulte [Visão geral do módulo](https://developer.adobe.com/commerce/php/architecture/modules/overview/) na documentação do desenvolvedor).

<pre>&lt;ExtraCountries>
 |
 &lt;etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 &lt;Plugin>
 | |
 | &lt;Framework>
 |   |
 |   &lt;Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 &lt;Setup>
 | |
 | &lt;Patch>
 |   |
 |   &lt;Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 composer.json
 registration.php</pre>

>[!NOTE]
>
>Cada seção de cabeçalho deste artigo descreve os arquivos da seção de estrutura do módulo.

## ExtraCountries/etc/config.xml

Uma nova configuração de módulo é definida neste arquivo XML. As configurações e tags a seguir podem ser editadas para ajustar as configurações padrão do novo país.

* `allow` - Para adicionar o país recém-adicionado à lista &quot;Países permitidos&quot; por padrão, anexe o novo Código do país ao final do conteúdo da tag `allow`. Os códigos de país são separados por vírgulas. Observe que essa marca substituirá os dados da marca *(Directory/etc/config.xml)* `allow` do arquivo de configuração do módulo `Directory`. É por isso que repetimos todos os códigos aqui além de adicionar o novo.
* `optional_zip_countries` - Se o CEP do país recém-adicionado for opcional, anexe o código do país ao final do conteúdo da marca `optional_zip_countries`. Os códigos de país são separados por vírgulas. Observe que essa marca substituirá os dados da marca *(Directory/etc/config.xml)* `optional_zip_countries` do arquivo de configuração do módulo `Directory`. É por isso que repetimos todos os códigos aqui além de adicionar o novo.
* `eu_countries` - Se o país recém-adicionado precisar fazer parte da lista de Países da União Europeia por padrão, anexe o código do país ao final do conteúdo da tag `eu_countries`. Os códigos de país são separados por vírgulas. Observe que essa marca substituirá os dados da marca *(\_Store/etc/config.xml\_)* `eu_countries` do arquivo de configuração do módulo `Store`. É por isso que repetimos todos os códigos aqui, além de adicionar um novo.
* Exemplo de arquivo `config.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

Para obter mais informações sobre os arquivos de configuração do módulo, consulte [Guia do desenvolvedor do PHP > Definir arquivos de configurações](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/) na documentação do desenvolvedor.

Observe que essas alterações são opcionais e afetarão somente o padrão pertencente ao novo país nas listas &quot;Permitir países&quot;, &quot;CEP/Código postal é opcional para&quot; e &quot;Países da União Europeia&quot;. Se este arquivo for ignorado na estrutura do módulo, um novo país ainda será adicionado, mas terá que ser configurado manualmente na página de configurações **Administração** > **Lojas** > *Configurações* > **Configuração** > **Geral** > **Opções de País**.

### ExtraCountries/etc/di.xml

O arquivo `di.xml` configura quais dependências são inseridas pelo gerenciador de objetos. Consulte <a>Guia do desenvolvedor do PHP > O di.xml</a> na documentação do desenvolvedor para obter mais detalhes sobre `di.xml`.

Em nosso exemplo, devemos registrar um `_TranslatedListsPlugin_` que traduzirá Códigos de país recém-introduzidos em Nomes de país completos, se os códigos não estiverem presentes nos dados de localização da Biblioteca de local Zend.

Exemplo de `di.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

No arquivo de registro do módulo, devemos especificar a dependência do módulo &quot;Diretório do Adobe Commerce&quot;, certificando-nos de que o módulo &quot;Países extras&quot; será registrado e executado após o módulo Diretório.

Consulte [Gerenciamento de dependências de módulo](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies) na documentação do desenvolvedor para obter mais informações sobre dependências de módulo.

Exemplo de `module.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

No método de plug-in `aroundGetCountryTranslation()`, devemos traduzir um código de país em um nome de país completo. Essa é uma etapa obrigatória para países que não têm um nome completo associado a um novo código de país na Biblioteca local Zend.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

Esse patch de dados será executado durante o processo de instalação/atualização do Adobe Commerce e adicionará um novo registro de país ao banco de dados.

Consulte [Desenvolver patches de dados e esquemas](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) na documentação do desenvolvedor para obter mais informações sobre patches de dados.

No exemplo abaixo, você pode ver que a matriz `$data` do método `apply()` contém os códigos de País ID, ISO2 e ISO3 para o novo país, e esses dados estão sendo inseridos no banco de dados.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

Este é um exemplo do arquivo registration.php. Para saber mais sobre o registro do módulo, consulte [Guia do Desenvolvedor do PHP > Registrar seu componente](https://developer.adobe.com/commerce/php/development/build/component-registration/) na documentação do desenvolvedor.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Este é um exemplo do arquivo composer.json.

Para saber mais sobre composer.json, consulte [Guia do desenvolvedor do PHP > O arquivo composer.json](https://developer.adobe.com/commerce/php/development/build/composer-integration/) em nossa documentação do desenvolvedor.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## Instalação do módulo

Para descobrir como instalar o módulo, consulte [Locais do módulo](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations) na documentação do desenvolvedor.

Depois que o diretório do módulo for colocado em um local correto, execute `bin/magento setup:upgrade` para aplicar os patches de dados e registrar o plug-in de tradução.

Talvez seja necessário limpar o cache do navegador para que as novas alterações funcionem.
