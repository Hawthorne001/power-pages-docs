---
title: Template tags
description: Learn about Liquid template tags available in Power Pages.
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

# Template tags

Template tags control the output of a template in various ways, and allow the combination of multiple templates into a single output.

## Fetchxml

Allows user to query data from Microsoft Dataverse, and render the results in a page.

> [!NOTE]
> You can learn more about querying the data using fetchxml at [use FetchXML to query data](/power-apps/developer/data-platform/use-fetchxml-construct-query).

```
{% fetchxml resultVariable %}
<!— Fetchxml query -->
...
{% endfetchxml %}
```

When using fetchxml to query data, ensure you don't use self-closing tags. For example, instead of `<attribute name="title"/>`, use `<attribute name="title"></attribute>` with explicit closure tag `</attribute>`.

### Results attribute

Results attribute in provided variable (such as 'resultVariable' in the previous sample) holds FetchXML query results and a few other attributes.

- *Entities*

    This attribute contains the result of fetchxml query. You can iterate the result and use it in your web template.

    ```
    <table> 
    {% for entityVariable in resultVariable.results.entities %} 
    <tr> 
    <td>Attribut-1: {{ entityVariable.attribute1 }}</td> 
    <td>Attribut-2: {{ entityVariable.attribute2 }}</td> 
    </tr> 
    {% endfor %} 
    </table> 
    ```

- *TableName*

    Gets the logical name of the entity.

- *ExtensionData*

    Gets the structure that contains extra data.

- *MinActiveRowVersion*

    Gets the lowest active row version value.

- *MoreRecords*

    Gets whether there are more records available.

- *PagingCookie*

    Gets the current paging information.

- *TotalRecordCount*

    Gets the total number of records in the collection. <br/>
    ReturnTotalRecordCount was true when the query was executed.

- *TotalRecordCountLimitExceeded*

    Gets whether the results of the query exceed the total record count.

### XML attribute

XML attribute in provided variable (such as 'resultVariable' in the previous sample) holds the resultant query that can be used to get data from Microsoft Dataverse. This attribute is useful for debugging purpose when you want to understand how table permission is getting applied on this *fetchxml* tag.  

### Other supported elements and attributes

Fetchxml liquid tag supports the following attributes, and child elements.

| Element/Child element | Attributes | Child element |
| - | - | - |
| fetch | mapping <br> version <br> count  <br> page  <br> paging-cookie  <br> utc-offset  <br> aggregate  <br> distinct  <br> min-active-row-version  <br> output-format  <br> returntotalrecordcount  <br> no-lock | order <br> entity |
| order | attribute <br> alias <br> descending | |
| entity | name <br> all-attributes <br> no-attrs <br> attribute | order <br> filter <br> link-entity |
| filter | type <br> hint <br> isquickfindfields | condition <br> filter |
| link-entity | name <br> from <br> to <br> alias <br> link-type <br> visible <br> intersect <br> all-attributes <br> no-attrs <br> attribute | order <br> filter <br> link-entity |
| condition | column <br> entityname <br> attribute <br> operator <br> aggregate <br> alias <br> uiname <br> uitype <br> uihidden <br> value | value |

## include

Includes the contents of one template in another, by name. In Power Pages, the source of this other template is generally a [web template](../web-templates.md). This operator allows for the reuse of common template fragments in multiple places.  

When a template is included in another, the included template has access to any variables defined in the parent template.

`{% include 'My Template' %}`

It's also possible to pass any number of named parameters to the include tag. These parameters are defined as variables in the included template.

`{% include 'My Template' a:x, b:y %}`

## block

Used with extends to provide template inheritance. See extends for usage.

## extends

Used with the block tag, provides template inheritance. This operator allows multiple templates to use a shared layout, while overriding specific areas of the parent layout.

In Power Pages, the parent template name provided to the tag generally refers to the name of a [web template](../web-templates.md).  

When extends is used, it must be the first content in the template, and can only be followed by one or more block tags.

If a block defined in the parent template isn't overridden, its contents in the parent template (if any) are rendered.

## comment

Allows you to leave unrendered code inside a Liquid template. Any content within the block aren't rendered, and any Liquid code within isn't executed.

**Code**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Output**

`Hello. My name is Charles.`

## raw

This feature lets you display Liquid code on a page without parsing or executing it.

**Output**

`Hello, {{ user.fullname }}. My name is Charles.`

## substitution

When you enable the header and footer caching, and want to avoid caching of certain section output, you can use this tag. This tag provides the content block in header or footer where output of the wrapped content block doesn't get cached. This operator is helpful in the scenarios where user is using an object that can frequently get updated, such as request, page, language, and date. For example, refer to the header and footer web template source code update scenarios when [header and footer caching is enabled](/power-apps/maker/portals/configure/enable-header-footer-output-caching).

> [!TIP]
> The URL used in [request.url](liquid-objects.md#request) can be any requested value, and gets [cached](/power-apps/maker/portals/configure/enable-header-footer-output-caching) for subsequent requests. To ensure correct value in request.url, consider using substitution tag, partial URL such as ~\{WebFile path} or storing the portal URL in [Site Settings](/power-apps/maker/portals/configure/configure-site-settings).

## codecomponent

See [Understand codecomponent Dataverse entity tag](dataverse-liquid-tags.md#codecomponent), [Use code components Liquid template tag](component-framework-liquid.md).

### See also

[Control flow tags](control-flow-tags.md)<br>
[Iteration tags](iteration-tags.md)<br>
[Variable tags](variable-tags.md)<br>
[Dataverse Liquid tags](dataverse-liquid-tags.md)<br>
[Use code components Liquid template tag](component-framework-liquid.md)

