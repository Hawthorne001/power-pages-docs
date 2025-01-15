---
title: Variable tags
description: Learn about variable tags available in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 01/15/2025
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - GitanjaliSingh33msft
---

# Variable tags

Variable tags are used to create new Liquid variables.

## assign

Creates a new variable. Assignments can also use [filters](liquid-filters.md) to modify the value.  

**Code**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Output**

```
It is valid.

DAVE BOWMAN
```

## capture

Captures the content within its block and assigns it to a variable. This content can then be rendered later by using output tags.

**Code**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Output**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### Related information

- [Control flow tags](control-flow-tags.md)
- [Iteration tags](iteration-tags.md)
- [Template tags](template-tags.md)
- [Dataverse Liquid tags](dataverse-liquid-tags.md)
