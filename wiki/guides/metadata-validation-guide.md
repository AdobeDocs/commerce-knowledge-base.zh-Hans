---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# 元数据验证指南

为了确保MD文件中元数据的格式正确，我们实施了元数据验证测试。 本文档提供的准则可帮助参与者避免一些最常见的元数据验证错误。

**元数据示例：**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## 常见验证错误以及如何避免/修复它们

以下是发生元数据验证错误的一些最常见方案。

### 元数据中的冒号

如果标题或标签或两者中都有冒号，则会发生验证错误。

**示例：**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

为避免此错误，请将标题或标签（如果两者均带有冒号，则两者）包裹在&#x200B;**单引号**&#x200B;中。

**示例：**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### 元数据中的冒号和单引号或撇号

如果标题或标签中存在冒号、单引号或撇号，则以前的解决方案将不起作用。

**示例：**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

通过将&#x200B;**双引号**&#x200B;中的标题或标签（或两者）换行来修复此错误。

**示例：**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### 元数据中的冒号、双引号和单引号或撇号

**示例：**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

发生这种情况时，请将标题或标签（或两者）包裹在&#x200B;**双引号**&#x200B;中，并使用&#x200B;**反斜杠**&#x200B;对标题和标签中的所有双引号进行转义。

**示例：**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### 元数据中缺少字段

如果元数据中缺少标题字段或标签字段，则会发生验证错误。

**示例：**

```markdown
---
title: This is a title
---
```

或者

```markdown
---
labels: article,labels,tags
---
```

要避免此错误，请在元数据中包含这两个字段。

标签字段可以留空，这不会导致错误，但必须填写标题字段。

**示例：**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
