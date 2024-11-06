---
title: “代码目录中无法保存类”错误
description: 本文介绍如何修复以下问题：指定依赖项的方式阻止即时自动生成类，并且您收到*“类无法保存在生成的/代码目录中”*错误消息。
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# “类无法保存在代码目录中”错误

本文介绍如何修复以下问题：指定依赖项的方式阻止即时自动生成类，并且您收到&#x200B;*“类无法保存在生成的/代码目录中”*&#x200B;错误消息。

## 受影响的产品和版本

* 云基础架构2.2.0或更高版本上的Adobe Commerce

## 问题

<u>重现步骤</u>

1. 在本地环境中，编写依赖于自动生成类的自定义类。
1. 运行触发自定义类的方案，并查看其是否正常运行。
1. 提交更改并将其推送到集成环境。 这将触发部署过程。 部署成功。
1. 在[集成环境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)中，运行触发自定义类的方案。

<u>预期的结果</u>

一切正常，就像在本地环境中一样。

<u>实际结果</u>

失败，错误消息指出您的类无法保存在`generated/code`目录中。

## 原因

问题的原因在于，您具有依赖关系的类不会在部署期间生成，并且无法在触发该类时稍后即时生成，因为在部署完成后，`generated/code`目录将无法写入。

发生这种情况有两个主要原因：

* 用例1：对自动生成类具有依赖关系的类位于入口点（如`index.php`）中，在部署期间不会扫描该入口点以确定依赖关系。
* 用例2：直接指定对自动生成类的依赖关系（与建议使用的构造函数声明依赖关系进行比较）。

## 解决方案

这两种情况的常见解决方案之一是创建一个真正的工厂，而不是自动生成类。

或者每个案例都有特定的解决方案。

### 案例1特定解决方案

将类代码从入口点移动到单独的模块，然后在入口点中使用它。

<u>示例</u>

中的原始代码，例如`index2.php` ：

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

您需要执行以下步骤：

1. 将类定义移动到`app/code/YourVendor/YourModule`：

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. 编辑入口点`my_api/index.php`，使其类似于以下内容：

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### 案例2特定解决方案

将依赖关系声明移动到构造函数。

<u>示例</u>

原始类声明：

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

您需要更改其构造函数，如下所示：

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## 相关阅读

* 在我们的开发人员文档中[代码生成](https://developer.adobe.com/commerce/php/development/components/code-generation/)。
