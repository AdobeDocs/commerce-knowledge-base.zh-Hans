---
title: 云站点运行缓慢
description: 本文提供了有关如何使云基础架构网站上的Adobe Commerce在重流量负载下表现更好的以及如何减少此负载的建议。
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# 云站点运行缓慢

本文提供了有关如何使云基础架构网站上的Adobe Commerce在重流量负载下表现更好的以及如何减少此负载的建议。

## 受影响的版本和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

<u>重现步骤</u>

1. 访问您的Adobe Commerce商店。
1. 浏览类别页面。
1. 将产品添加到购物车。

<u>预期的结果</u>

网站响应迅速，向购物车添加产品非常迅速。

<u>实际结果</u>

网站速度慢，或者类别页面快但购物车页面慢。

## 调试步骤和解决方案

执行以下步骤来跟踪性能缓慢的原因并进行修复。 您可以切换第一个和第二个步骤，但只有在缓存设置优化没有帮助时才继续阻止IP。

1. 检查高流量页面的缓存命中率，并减少高度更新的数据量。
1. 检查总体站点缓存命中率并验证常规缓存/Fastly配置。
1. 识别导致高服务器负载的Web客户端并阻止IP导致高负载。

以下段落提供了每个步骤的更多详细信息。

### 步骤1：检查高流量页面的缓存命中率

修复受高流量困扰的网站的第一步是确保正确缓存流量最大的页面，如商店的主页和顶级类别页面。

您可以通过查看使用cURL的`X-Cache` HTTP标头来确定这些页面的缓存命中率，如Fastly文档中的[使用cURL检查缓存](https://docs.fastly.com/guides/debugging/checking-cache#using-curl)中所述。 或者，使用您最喜爱的Web浏览器的开发人员工具栏中的“网络”选项卡检查相同的标头。

Fastly通常遵循来自应用程序的响应标头；但是，如果标头都设置为“不缓存”并且页面“过去过期”，则Fastly无法缓存页面。

>[!WARNING]
>
>请注意，Fastly会更改响应标头，因此使用cURL或Web浏览器检查主URL不一定会显示应用程序发出了哪些标头。 Fastly本身通常使用“无缓存”标头响应Web浏览器，但Web应用程序本身允许缓存，并且Fastly可以正确缓存项目。 因此，“cache-control”和“pragma”标头信息在此情况下将不起作用。

#### 高流量页面的疑难解答

如果索引页的点击率较低，您可以通过减少该页上存在的严重更新数据量来修复此问题。

### 步骤2：检查总体网站缓存命中率

要检查总体缓存命中率，请执行以下操作：

1. 在云基础架构环境中[获取Adobe Commerce的Fastly凭据](http://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#cloud-fastly-creds)。
1. 运行以下Linux/macOS cURL命令以检查网站在过去30分钟内的点击率，并用您的Fastly凭据的值替换和：

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   您还可以通过将时间范围查询选项从`?by=minute`更改为`?by=hour`或`?by=day`，检查过去一天或一个月内的历史点击率。 有关获取Fastly缓存统计信息的详细信息，请参阅Fastly文档中的[查询选项](https://docs.fastly.com/api/stats#Query)。

   `| json_pp`选项使用`json_pp`实用工具漂亮地打印JSON响应输出。 如果您收到_&#39;json\_pp not found&#39;_错误，请安装`json_pp`实用程序，或使用其他命令行工具进行JSON美化打印。 或者，删除`| json_pp`参数并再次运行该命令。 JSON响应输出的格式不正确，但您可以通过JSON修饰符运行它以对其进行清理。

命中率高于0.90或90%表示全页缓存运行正常。

命中率低于0.85或85%可能表示站点配置有问题，或者您可能安装了不允许缓存其内容的第三方扩展。

#### 整体缓存命中率的疑难解答

1. 使用每小时和每日命中率统计信息，确定命中率何时开始下降。 如果在您将更改部署到网站的同一时间左右，点击率突然下降，请考虑回退更改，直到网站负载下降。
1. 在Commerce管理员的&#x200B;**存储** > **配置** >高级> **系统** > **全页缓存**&#x200B;下检查配置。 确保公共内容&#x200B;**值的** TTL设置得不是太低。
1. 确保已[上传VCL代码片段](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets)。
1. 如果使用自定义VCL代码片段，请对其进行调试以正确使用“通过”或“管道”操作：应谨慎使用这些代码片段，并且至少应将其用于某种条件。 有关更多提示，请参阅我们的开发人员文档中的[自定义Fastly VCL代码片段](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-vcl-custom-snippets.html)。

### 步骤3：识别导致服务器负载过高的网站

您可以使用以下任一方法获取有关访问Adobe Commerce存储的IP地址的信息。

* 通过SSH会话检查HTTP访问日志。
* 请联系Adobe Commerce支持以请求一个IP地址列表，这会造成站点负载过重。

#### 检查HTTP访问日志

要查看站点的访问日志，请从本地开发环境中运行以下命令：

```bash
magento-cloud log access
```

使用查看更多行

```bash
--lines
```

选项，例如：

```bash
magento-cloud log access --lines=500
```

您可以查看此日志，并查看大部分请求是否来自特定IP地址。 另一种方法是使用`awk` 、 `sort`和`uniq`自动计算日志中最常出现的IP地址，如下所示：

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

如果

```bash
magento-cloud log
```

命令不起作用，您可以使用SSH连接到远程服务器并检查位于`/var/log/access.log`的日志文件

在识别导致服务器负载较重的IP地址后，可以通过从Commerce管理面板的&#x200B;**存储** > **配置** >高级> **系统** > **全页缓存** > **快速配置** > **阻止**&#x200B;下配置IP阻止列表来阻止它们。

如果由于负载较重而无法访问管理员，则可以使用Fastly API设置阻止规则：

1. 按照[使用API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly文档处理ACL中的说明创建ACL。
1. 在`recv`部分中，创建一个包含以下内容的VCL片段，该片段已将ACL\_NAME\_GOES\_HERE替换为上一步中创建的ACL的名称：

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

有关阻止IP地址的详细信息，请参阅GitHub中的[Fastly Adobe Commerce模块指南](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)。
