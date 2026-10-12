---
title: '[!DNL Live Search]仪表板和搜索结果排名不正确'
description: 如果[!DNL Live Search]仪表板中的数据不正确，或者搜索结果的排名与预期不符，本文将提供故障排除信息。
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# [!DNL Live Search]仪表板和搜索结果排名不正确

如果您发现[!DNL Live Search]仪表板中显示的数据不正确，或者搜索结果[排名](https://experienceleague.adobe.com/zh-hans/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies)与预期不符，请查看以下内容，可能原因如下：

* `productView`事件中产品上下文的`topLevelSku`字段缺失。 这会导致空转化和其他意外量度。

* `add-to-cart`事件未设置并填充`productContext`字段。

* 环境类型不正确。 例如，如果将环境设置为&#x200B;*[!UICONTROL Testing]*&#x200B;而不是&#x200B;*[!UICONTROL Production]*。 有关详细信息，请参阅[店面上下文](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md)。

* [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md)事件中缺少搜索结果上下文。
