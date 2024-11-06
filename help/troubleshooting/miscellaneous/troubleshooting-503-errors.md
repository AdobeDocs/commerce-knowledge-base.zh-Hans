---
title: 由于必须更改默认清漆设置而导致503错误故障诊断
description: 本文提供了一些解决方案，用于解决由于某些清漆缓存默认值不足以存储而导致的503错误。
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 由于必须更改默认清漆设置而导致503错误故障诊断

本文提供了一些解决方案，用于解决由于某些清漆缓存默认值不足以存储而导致的503错误。

## 问题

如果Adobe Commerce使用的缓存标记长度超过Varnish的默认值8192字节，则可以在浏览器中看到HTTP 503（后端提取失败）错误。 错误可能显示类似于以下内容： *”错误503后端获取失败。 后端获取失败“*”

## 解决方案

要解决此问题，请增加Varnish配置文件中`http_resp_hdr_len`参数的默认值。 `http_resp_hdr_len`参数指定最大标头长度&#x200B;*在*&#x200B;之内，默认响应总大小为32768字节。

>[!NOTE]
>
>如果`http_resp_hdr_len`值超过32K，还必须使用`http_resp_size`参数增加默认响应大小。

1. 作为具有`root`权限的用户，在文本编辑器中打开“消失”配置文件：
   * CentOS 6： `/etc/sysconfig/varnish`
   * CentOS 7： `/etc/varnish/varnish.params`
   * Debian： `/etc/default/varnish`
   * Ubuntu： `/etc/default/varnish`
1. 搜索`http_resp_hdr_len`参数。
1. 如果参数不存在，请将其添加到`thread_pool_max`之后。
1. 将`http_resp_hdr_len`设置为一个值，该值等于最大类别的产品数乘以21。 （每个产品标记的长度约为21个字符。）    例如，如果最大类别具有3,000个产品，则将该值设置为65536字节应有效。    例如：    ```conf    -p http_resp_hdr_len=65536 \    ```
1. 将`http_resp_size`设置为适应增加的响应标头长度的值。    例如，使用增加的标头长度和默认响应大小的总和是一个良好的起点(例如，65536 + 32768 = 98304)： `-p http_resp_size=98304`。 以下是一个代码片段：

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## 运行状况检查超时 {#health-check-timeouts}

如果在Varnish配置为缓存应用程序时禁用缓存，并且当Adobe Commerce处于开发人员模式时，可能无法登录到管理员。

由于默认运行状况检查的`timeout`值为2秒，因此可能发生这种情况。 运行状况检查可能需要2秒以上的时间来收集和合并有关每个运行状况检查请求的信息。 如果在10次运行状况检查中有6次出现这种情况，则认为Adobe Commerce服务器不正常。 当服务器不正常时，清漆会提供过时的内容。

由于管理员是通过Varnish访问的，因此您无法登录到管理员以启用缓存(除非Adobe Commerce再次正常运行)。 但是，可以使用以下命令启用缓存：

```bash
$ bin/magento cache:enable
```

有关使用命令行的详细信息，请参阅[命令行配置入门](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli)。
