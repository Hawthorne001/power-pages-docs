---
title: Replace default copilot with a copilot customized using Microsoft Copilot Studio
description: Learn how to replace the default Power Pages copilot with another copilot available in Microsoft Copilot Studio.
ms.topic: how-to
ms.date: 08/30/2024
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom: bap-template
ms.collection: 
    - bap-ai-copilot
---

# Replace default copilot with a copilot customized using Microsoft Copilot Studio

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

This article offers a comprehensive, step-by-step guide for updating default Power Pages copilot with another copilot available in Microsoft Copilot Studio.

## Prerequisites

- You must have a copilot created in [Microsoft Copilot Studio](/microsoft-copilot-studio/nlu-gpt-quickstart#create-a-boosted-bot).

- [Copilot](enable-chatbot.md#add-a-copilot) must be created and published in the site where you're updating another copilot available in Microsoft Copilot Studio.

- Only a copilot with [No authentication](/microsoft-copilot-studio/configuration-end-user-authentication#no-authentication) can be replaced.

## Copy the copilot schema name

1. Sign in to [Microsoft Copilot Studio](https://web.powerva.microsoft.com/).

1. Select the copilot you want to use in Power Pages.

1. Navigate to **Copilot details** under **Settings**.

1. Select **Advanced** tab.

1. Copy the **Schema name**.

## Verify Data model version

Copilot can be enabled for both Standard and Enhanced site data model. The steps to replace it vary based on the data model. Make sure you're following the right steps based on the data model.

1. Go to the [Set up workspace](../configure/setup-workspace.md).

1. Select **Site details**.

1. Verify the **Data Model** version. You can choose **Standard** or **Enhanced**.

## Update the copilot based on your data model version

Choose the following tab, which corresponds to your data model, to see the appropriate steps.

# [Standard data model](#tab/standard)

1. Go to the [Data workspace](use-data-workspace.md).
1. Search for and select the **Bot consumer** table.
1. Locate the row with the selected website name.
1. Replace the Schema Name column value with the new schema name you copied earlier.

# [Enhanced data model](#tab/enhanced)

1. Go to the [Data workspace](use-data-workspace.md).
1. Search for and select the **Site Component** table.
1. Find the **Component Type** column and select the filter icon next to it.
1. Filter records by **Bot Consumer** option.
1. Locate the row with the selected website name in the **Power Pages Site id** column.
1. Choose **Edit row using form**.
1. Within **Content**, update the **botschemaname** json value with the new schema name you copied earlier.

    :::image type="content" source="media/pva-bot-how-to/bot-enhanced-data-model.png" alt-text="A screenshot of the General options for Bot Consumer with the botschemaname json value emphasized.":::

1. Choose **Save & Close**.

---
