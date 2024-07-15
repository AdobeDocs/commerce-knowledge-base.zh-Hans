---
title: 'Adobe Commerce 2.4.0已知问题：集成测试失败'
description: 本文为Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致集成测试失败，因为“Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest：：setup()”的声明与用于2.4.0的PHPUnit 9不兼容。
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知问题：集成测试失败

本文为Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致集成测试失败，因为`Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()`的声明与用于2.4.0的PHPUnit 9不兼容。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 问题

<u>重现步骤</u>

运行2.4.0集成测试

<u>预期的结果</u>

测试通过。

<u>实际结果</u>

*PHP致命错误：Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest：：setup()的声明必须与PHPUnit\\Framework\\TestCase：：setup()： /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php中的第36*&#x200B;行空白

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
