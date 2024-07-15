---
title: 'MDVA-37288：GraphQL请求后返回错误的层价格'
description: 适用于Adobe Commerce的MDVA-37288质量修补程序解决了在GraphQL请求后返回错误层价格的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: d2cf24d5-6163-4968-a89c-b7407d439e1c
feature: GraphQL, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-37288：GraphQL请求后返回了错误的层价格

适用于Adobe Commerce的MDVA-37288质量修补程序解决了在GraphQL请求后返回错误层价格的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23时，此修补程序可用。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.4.2设计的
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.4.2上的Adobe Commerce

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 将层定价添加到任何项目（例如，将层价格添加到ID=1和ID=2的项目）。
1. 通过搜索运行GraphQL查询，其中将包括具有层价格的项目和不具有层价格的项目。

<pre><code class="language-graphql">
{
  products(pageSize: 20, currentPage: 1, search: "24-MB0") {
    items {
      id
      price_tiers {
        quantity
        final_price {
          value
        }
      }
    }
  }
}
</code></pre>

<u>预期的结果</u>：

只有具有层级价格的项目才应返回适当的层级价格：

```json
{
  "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": []
                },
                {
                    "id": 19,
                    "price_tiers": []
                }
            ]
        }
    }
}
```

<u>实际结果</u>：

* 在响应中，所有以层定价的项目后续显示的项目都具有层定价。
* 它返回的分层定价数据来自循环中具有分层定价的最后一个项目。

响应示例：

```json
{
    "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 19,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```


## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品，在我们的开发人员文档中使用以下链接：

* Adobe Commerce和Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相关阅读

要在我们的支持知识库中了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

有关QPT工具中可用的其他修补程序的信息，请参阅我们的支持知识库中的[QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)部分。
