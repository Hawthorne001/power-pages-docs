---
title: Available Liquid tags
description: Learn about the available liquid tags in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 01/09/2023
ms.subservice:
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - GitanjaliSingh33msft
---

# Available Liquid tags

Tags make up the programming logic that tells templates what to do. Tags are wrapped in {% %}.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## White space control

Normally, Liquid renders everything outside of variable and tag blocks verbatim, with all the white space as-is. Occasionally you don't want the extra white space, but you still want to format the template cleanly, which requires white space.

You can tell the engine to strip all leading or trailing white space by adding a hyphen (-) to the start or end block tag.

**Code**

```
{% for i in (1..5) -%}

{{ i }}

{%- endfor %}
```

**Output**

```
12345
```
### See also

[Liquid types](liquid-types.md)  
[Liquid Objects](liquid-objects.md)  
[Liquid Filters](liquid-filters.md) 


