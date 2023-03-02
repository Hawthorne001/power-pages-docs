---
title: "Tutorial: How to add a rich text component to a form"
description: Walk-through example steps for adding a rich text component to a form in Power Pages.
author: GitanjaliSingh33msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: 
ms.date: 03/02/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
  - nickdoelman
  - GitanjaliSingh33msft

---

# Tutorial: Configure the rich text editor control on Power Pages 

In the tutorial, you'll configure the rich text editor component on a Microsoft Dataverse form, and enable the rich text editor to be visible on a webpage.

This tutorial will use the **Feedback** table and the **Contact us** webpage that is available in the **Starter layout** templates.

## Prerequisites

- Your portal version must be [9.4.3.x](/power-platform/released-versions/portals) or later.
- A site using one of the **Starter layout** [templates](../templates/site-design.md).

## Step 1. Add the code component to a field in a form

1. In the design studio, select the [Data workspace](../getting-started/use-data-workspace.md).

1. Select the **Feedback** table.

1. Select **Forms** and then choose to edit the **simple contact us form**.

1. Select the **Message** field.

1. Choose **+ Component** and select the **Number input** component.

    :::image type="content" source="media/component-rte-tutorial/add-rte-component.png" alt-text="Add RTE component to form.":::

1. Select **Done**.

1. Select **Save** and **Publish form**.

## Step 2. Configure the rich text editor component on webpage

In the following steps we will configure the existing feedback page, you can also [create your own page](../getting-started/first-page.md) and add your own [form](../getting-started/add-form.md) component.

1. In the **Pages** workspace, select the **Contact us** page.

1. The **Message** field should appear on the form with the message **Enable custom component to see this field in preview**.

1. Select the field and choose **Edit field**.

1. Select the **Enable custom component** field.

    :::image type="content" source="media/component-rte-tutorial/enable-rte-on-form.png" alt-text="Enable RTE component in design studio.":::

1. Select **OK**.

1. Select **Sync**.

> [!NOTE]
> To display the data as rich text, you might have to increase the character size of the text columns to accommodate the extra information.

## Step 3.1 Add table permissions for the rich text attachment table

For using and storing images in the rich text editor on the portal, you'll need to add [table permissions](../security/table-permissions.md) to the rich text attachment table (msdyn_richtextfile).

1. Open the design studio and select **Set up** workspace.

1. Select **Table permissions**.

1. Select **+ New permission** to create a new table permission for the rich text attachment table. The name can be anything you choose; in this example, we use **RTE Attachment**.

1. For **Access type**, select **Global access**.

    > [!NOTE]
    > The **Global access** type is chosen because no relationship exists between the table configured to use the rich text editor control and the rich text attachment table.

1. Under **Permission to**, select the **Read**, **Write**, **Create**, and **Delete** checkboxes.
 
1. Assign an appropriate [web role](../security/create-web-roles.md) to the table permission.

    :::image type="content" source="media/component-rte-tutorial/rich-text-table-permission.png" alt-text="Configuration of the rich text table permissions.":::

> [!IMPORTANT]
> If you want to store images as base 64 strings directly in the column that you've configured to use the rich text editor control, you need to configure the control by using a [JSON configuration file](/power-apps/maker/model-driven-apps/rich-text-editor-control#create-and-use-advanced-configuration-for-the-rich-text-editor-control). Set **disableImages** and **disableDefaultImageProcessing** to **true** to allow images to be rendered consistently across all clients. Using this method doesn't require the global table permission on the rich text attachment (msdyn_richtextfile) table.

## Step 3.2. Add web API site setting

In order to save images in the rich text editor control, you will need to add a couple of site settings.

1. Open the [Portals Management app](portal-management-app.md). 

1. Go to **Site Settings**.

1. Create the following site settings: enter the name, your website, and the value of **true**, and then select **Save & Close**.

    | Site setting name | Value |
    | - | - | 
    | Webapi/msdyn_richtextfile/enabled | true |
    | Webapi/msdyn_richtextfile/fields | * |


## Step 4. Preview the site.

1. In the design studio, select **Sync**.

1. Select **Preview** and then select **Desktop**, go to the **Contact us** page, you should see the custom component enabled.

    :::image type="content" source="media/component-rte-tutorial/rich-text-editor-on-form.png" alt-text="RTE component on a form.":::

## Rich text editor on a read-only form

On a read-only form, the rich text editor displays the content with formatting and images. The content can be read, but not edited or updated.

### See also

- [Power Apps component framework overview](/power-apps/developer/component-framework/overview) 
- [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript) 
- [Add code components to a field or table in model-driven apps](/power-apps/developer/component-framework/add-custom-controls-to-a-field-or-entity)
