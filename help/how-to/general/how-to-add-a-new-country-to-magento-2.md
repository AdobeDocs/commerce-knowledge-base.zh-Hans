---
title: 如何向Adobe Commerce添加新国家/地区
description: 本文介绍如何添加Adobe Commerce和Zend区域设置库中不存在的国家/地区。 这需要根据适用的协议条款对代码和数据库进行更改，以构成客户自定义项。 请注意，本文中包含的示例材料按“原样”提供，不提供任何形式的担保。 Adobe或任何关联实体均无义务维护、更正、更新、更改、修改或以其他方式支持这些材料。 在这里，我们将描述为实现这一目标需要做的工作的基本原则。
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# 如何向Adobe Commerce添加新国家/地区

本文介绍如何添加Adobe Commerce和Zend区域设置库中不存在的国家/地区。 这需要根据适用的协议条款对代码和数据库进行更改，以构成客户自定义项。 请注意，本文中包含的示例材料按“原样”提供，不提供任何形式的担保。 Adobe或任何关联实体均无义务维护、更正、更新、更改、修改或以其他方式支持这些材料。 在这里，我们将描述为实现这一目标需要做的工作的基本原则。

在本例中，我们使用在Adobe Commerce安装或升级过程中应用的数据修补程序创建新的Adobe Commerce模块，并将国家/地区代码为XX的抽象国家/地区添加到Adobe Commerce。 [Adobe Commerce Directory](https://developer.adobe.com/commerce/php/module-reference/module-directory/)构建初始国家/地区列表，然后使用设置修补程序将地区附加到该列表。 本文介绍如何创建新模块，以将新国家/地区附加到列表。 您可以查看现有Adobe Commerce Directory模块的代码以供参考。 这是因为以下示例模块继续进行构建国家/地区列表的目录模块作业，并重复使用Adobe Commerce目录模块安装补丁程序的部分代码。

## 推荐文档

您必须熟悉Adobe Commerce模块开发，才能创建一个新的模块。

在尝试创建新模块之前，请参阅我们的开发人员文档中的以下主题：

* [PHP开发人员指南](https://developer.adobe.com/commerce/php/development/)
* [模块概述](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [创建新模块](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/create-module)
* [模块配置文件](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)

## 所需信息

新的国家/地区在Adobe Commerce中必须具有唯一的名称、国家/地区ID、ISO2和ISO3代码。

## 模块结构

在此示例中，我们将创建一个名为\&#39;ExtraCountries\&#39;的新模块，该模块具有以下目录结构：

（要了解有关模块结构的更多信息，请参阅我们的开发人员文档中的[模块概述](https://developer.adobe.com/commerce/php/architecture/modules/overview/)）。

<pre><ExtraCountries>
 |
 <etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 <Plugin>
 | |
 | <Framework>
 |   |
 |   <Locale>
 |     |
 |     TranslatedListPlugin.php
 |
 <Setup>
 | |
 | <Patch>
 |   |
 |   <Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 composer.json
 registration.php</pre>

>[!NOTE]
>
>本文的每个标题部分都介绍了模块结构部分中的文件。

## ExtraCountries/etc/config.xml

新的模块配置在此XML文件中定义。 可以编辑以下配置和标记，以调整新的国家/地区默认设置。

* `allow` — 要将新添加的国家/地区默认添加到“允许国家/地区”列表，请将新的国家/地区代码附加到`allow`标记内容的末尾。 国家/地区代码以逗号分隔。 请注意，此标记将覆盖`Directory`模块配置文件&#x200B;*(Directory/etc/config.xml)* `allow`标记中的数据，因此我们会重复此处的所有代码并添加新的代码。
* `optional_zip_countries` — 如果新添加国家/地区的邮政编码应为可选，请将国家/地区代码附加到`optional_zip_countries`标记内容的末尾。 国家/地区代码以逗号分隔。 请注意，此标记将覆盖`Directory`模块配置文件&#x200B;*(Directory/etc/config.xml)* `optional_zip_countries`标记中的数据，因此我们会重复此处的所有代码并添加新的代码。
* `eu_countries` — 默认情况下，如果新添加的国家/地区必须是欧盟国家/地区列表的一部分，请将国家/地区代码附加到`eu_countries`标记内容的末尾。 国家/地区代码以逗号分隔。 请注意，此标记将覆盖`Store`模块配置文件&#x200B;*(\_Store/etc/config.xml\_)* `eu_countries`标记中的数据，因此我们会重复此处的所有代码并添加新的代码。
* `config.xml`文件示例

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

有关模块配置文件的详细信息，请参阅我们的开发人员文档中的[PHP Developer Guide > Define Configurations files](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/)。

请注意，这些更改是可选的，只会影响新国家/地区的默认属于“允许国家/地区”、“邮政编码对于是可选的”和“欧盟国家/地区”列表。 如果从模块结构跳过了此文件，则仍会添加新的国家/地区，但必须在&#x200B;**管理员** > **商店** > *设置* > **配置** > **常规** > **国家/地区选项**&#x200B;设置页面中手动配置此文件。

### ExtraCountries/etc/di.xml

`di.xml`文件配置对象管理器插入的依赖项。 有关`di.xml`的更多详细信息，请参阅我们的开发人员文档中的<a>PHP开发人员指南> di.xml</a>。

在我们的示例中，如果Zend区域设置库本地化数据中不存在代码，则必须注册一个`_TranslatedListsPlugin_`，以便将新引入的国家/地区代码转换为完整的国家/地区名称。

`di.xml`示例

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

在模块注册文件中，我们必须为“Adobe Commerce目录”模块指定依赖关系，确保在“目录”模块之后注册并执行“额外国家/地区”模块。

有关模块依赖项的更多信息，请参阅我们的开发人员文档中的[管理模块依赖项](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies)。

`module.xml`示例

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

在`aroundGetCountryTranslation()`插件方法中，必须将国家/地区代码转换为国家/地区完整名称。 对于在Zend区域设置库中没有与新国家/地区代码相关联的全名的国家/地区，这是必需的步骤。

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

此数据修补程序将在Adobe Commerce安装/升级过程中执行，并将向数据库中添加新的国家/地区记录。

有关数据修补程序的详细信息，请参阅我们的开发人员文档中的[开发数据和架构修补程序](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/)。

在下面的示例中，您可以看到方法`apply()`的`$data`数组包含新国家/地区的国家/地区ID、ISO2和ISO3代码，并且此数据正在插入到数据库中。

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

这是registration.php文件的一个示例。 要了解有关模块注册的更多信息，请参阅我们的开发人员文档中的[PHP Developer Guide > Register your component](https://developer.adobe.com/commerce/php/development/build/component-registration/)。

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

这是composer.json文件的一个示例。

要了解有关composer.json的更多信息，请参阅我们的开发人员文档中的[PHP开发人员指南> Composer.json文件](https://developer.adobe.com/commerce/php/development/build/composer-integration/)。

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

## 模块安装

要了解如何安装模块，请参阅我们的开发人员文档中的[模块位置](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations)。

将模块目录放置到正确位置后，执行`bin/magento setup:upgrade`以应用数据修补程序并注册翻译插件。

您可能需要清除浏览器缓存，新更改才能生效。
