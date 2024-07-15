---
title: 404执行目录价格规则计划更新后商店前端出错
description: 本文介绍了在创建目录价格规则更新并稍后编辑其开始时间后，修复与在所有商店主页中出现404错误相关的已知Adobe Commerce 2.2.1问题的补丁程序和所需步骤。 要解决此问题，您需要应用修补程序。
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404执行目录价格规则计划更新后商店前端出错

本文介绍了在创建目录价格规则更新并稍后编辑其开始时间后，修复与在所有商店主页中出现404错误相关的已知Adobe Commerce 2.2.1问题的补丁程序和所需步骤。 要解决此问题，您需要应用修补程序。

## 问题

店面页面不可用，返回404错误。 如果初始创建后编辑了此更新的开始日期，则在活动目录价格规则更新到期后会出现问题。

<u>重现步骤</u>：

1. 在Commerce管理员中，在&#x200B;**营销** > **促销活动** > **目录价格规则**&#x200B;下创建新的目录价格规则。
1. 在&#x200B;**目录价格规则**&#x200B;网格中，单击&#x200B;**编辑，**&#x200B;计划新的更新并将&#x200B;**状态**&#x200B;设置为&#x200B;*活动。*
1. 导航到&#x200B;**内容** > **内容暂存** > **仪表板。**
1. 选择最近创建的更新并更改其开始时间。
1. 保存更改。

<u>预期的结果</u> ：

当“更新”起始日期生效时，目录价格规则将应用成功。

<u>实际结果</u> ：

当更新开始日期生效时，店面中的所有目录和产品将变得不可用，并返回404错误。

## 解决方案

要恢复目录页并能够完全使用目录价格规则更新功能，您需要安装修补程序，手动和管理员中删除规则，并修复数据库中的无效链接。 您还需要重新创建目录价格规则。

以下是所需步骤的详细说明：

1. [应用修补程序](#patch)。
1. 在Commerce管理员中，删除与问题（其开始时间已更新）相关的目录价格规则。 为此，请在&#x200B;**营销** > **促销活动** > **目录价格规则**&#x200B;下打开规则页面，然后单击&#x200B;**删除规则**。
1. 访问数据库手动从`catalogrule`表中删除相关记录。
1. 修复数据库中的无效链接。 有关详细信息，请参阅[相关段落](#fix_links)。
1. 在&#x200B;**营销**&#x200B;下的Commerce管理员中，转到&#x200B;**促销活动** > **目录价格规则**，然后使用所需的配置创建新规则。
1. 清除&#x200B;**系统** > **缓存管理**&#x200B;下的浏览器缓存。
1. 确保cron作业配置正确并且可以成功执行。

## Patch {#patch}

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce 2.2.1

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.2.0 - 2.2.4
* Adobe Commerce内部部署2.2.0和2.2.2 - 2.2.4

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 修复指向数据库中暂存的无效链接 {#fix_links}

>[!WARNING]
>
>我们强烈建议在任何数据库操作之前创建数据库备份。 我们还建议先在开发环境中测试查询。

执行以下步骤来修复具有指向`staging_update`表的无效链接的行。

1. 检查`flag`表中是否存在指向`staging_update`表的无效链接。 这些是`flag_code=staging`的记录。
1. 使用以下查询识别`flag`表中的无效版本：

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. 从`staging_update`表中，选择小于当前（无效）版本的现有版本，并获取返回两个数字的版本值。 您采用此版本，而不是以前的版本，以避免出现上一个版本是`staging_update`表中可应用的最大版本的情况，我们仍需要重新应用它。

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   您收到的响应版本是您的有效版本`id`。

1. 对于`flag`表中具有无效链接的行，请将`flag_data`值设置为包含有效版本ID的数据。 这有助于保存重新索引步骤的性能，并允许避免重新索引所有实体。

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>示例：</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## 附加文件
