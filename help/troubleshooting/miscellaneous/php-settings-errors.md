---
title: PHP设置错误
description: 本文为PHP设置错误提供了解决方案。
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# PHP设置错误

本文为PHP设置错误提供了解决方案。

## PHP内存限制错误

准备情况检查确保您至少为PHP进程预留了1GB的内存。 对于大多数安装（包括安装可选的示例数据），此设置应该已经足够。 但是，我们建议至少使用2 GB进行调试。

要增加PHP内存限制，请执行以下操作：

1. 登录到您的Adobe Commerce服务器。
1. 使用以下命令查找`php.ini`文件：

   ```
   bash    $ php --ini
   ```

1. 作为具有`root`权限的用户，请使用文本编辑器打开`Loaded Configuration File`指定的`php.ini`。
1. 找到`memory_limit`。
1. 将其更改为值`2GB`以供正常使用和调试。
1. 将更改保存到`php.ini`并退出文本编辑器。
1. 重新启动Web服务器。 示例如下：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`
   * nginx（CentOS和Ubuntu）： `service nginx restart`

1. 请重试安装。

## 由于表单过大，出现最大输入变量错误

具有大量存储审阅、产品、属性或选项的配置可以生成超过预设PHP限制的表单。 如果发送的值数超过`php.ini`内设置的`max-input-vars`限制（默认值为1000），则不会传输剩余数据，也不会更新这些数据库值。 发生这种情况时，PHP日志中会出现警告：

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

`max-input-vars`没有“适当”值；这取决于配置的大小和复杂性。 根据需要修改`php.ini`文件中的值。 请参阅[必需的PHP设置](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/php-settings)。

## xdebug最大函数嵌套级别错误

请参阅[在安装期间，xdebug最大函数嵌套级别错误](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md)。

## 访问PHTML模板时显示错误

错误文本通常为：

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### 解决方案：在php.ini中设置`asp_tags = off`

多个模板具有支持包装在`<% %>`标记中的模板抽象级别的语法（使用不同的模板引擎，如Twig），如用于显示产品图像的这个[模板](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml)：

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

有关[asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags)的详细信息。

编辑`php.ini`并设置`asp_tags = off`。 有关详细信息，请参阅[必需的PHP设置](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/php-settings)。
