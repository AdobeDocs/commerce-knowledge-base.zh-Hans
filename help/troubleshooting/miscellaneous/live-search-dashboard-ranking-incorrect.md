---
title: “[!DNL Live Search]仪表板和搜索结果排名不正确”
description: 如果 [!DNL Live Search] 仪表板中的数据不正确，或者搜索结果的排名与预期不符，本文将提供故障排除信息。
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search]仪表板和搜索结果排名不正确

如果您发现[!DNL Live Search]仪表板中显示的数据不正确，或者搜索结果[排名](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies)与预期不符，请查看以下内容，可能原因如下：

* `productView`事件中产品上下文的`topLevelSku`字段缺失。 这会导致空转化和其他意外量度。

* `add-to-cart`事件未设置并填充`productContext`字段。

* 环境类型不正确。 例如，如果将环境设置为&#x200B;*[!UICONTROL Testing]*&#x200B;而不是&#x200B;*[!UICONTROL Production]*。 有关详细信息，请参阅[店面上下文](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md)。

* [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md)事件中缺少搜索结果上下文。
