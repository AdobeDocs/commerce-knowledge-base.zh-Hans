---
title: 'Adobe Commerce内部部署2.4.2：产品图像缺失'
description: 本文介绍了一个已知的Adobe Commerce内部部署2.4.2问题，该问题导致产品图像未上传到产品页面。 此问题计划在版本2.4.3之后的未来版本中解决。目前没有可用的解决方案，但作为解决方法，您可以禁用Nginx来调整图像大小。
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce内部部署2.4.2：产品图像缺失

本文介绍了一个已知的Adobe Commerce内部部署2.4.2问题，该问题导致产品图像未上传到产品页面。 此问题计划在版本2.4.3之后的未来版本中解决。目前没有可用的解决方案，但作为解决方法，您可以禁用Nginx来调整图像大小。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.2

## 问题

产品图像保存在`s3`存储桶中，但未同步回`pub/media`目录。 仅当同时使用以下两种方式时，才会出现此问题：

* 启用网站的Nginx可调整图像大小
* AWS `s3`作为媒体存储空间

<u>先决条件</u>：

Adobe Commerce与Nginx一起安装。

<u>重现步骤</u>：

1. 将Adobe Commerce配置为使用AWS `s3`作为媒体存储。
1. 使用Adobe Commerce安装目录中提供的`nginx.conf.sample`配置文件和Nginx虚拟主机配置Nginx。 请参阅我们的开发人员文档中的[配置Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu)。
1. 创建一个具有一个产品映像的简单产品。
1. Nginx在`nginx.conf.sample`中调整图像大小的配置未注释，类似于以下内容：

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>预期的结果</u>：

产品图像将上传到产品页面。

<u>实际结果</u>：

产品图像未上传到产品页面。

## 解决方法

禁用Nginx以调整图像大小。
