---
title: Configure managed rules in Power Pages WAF
description: Learn how to configure managed rules and bot protection in Power Pages Web Application Firewall (WAF) to secure your site from threats and automated bots.
author: shwetamurkute
contributors:
ms.topic: concept-article
ms.date: 06/30/2025
ms.author: nabha
ms.reviewer: smurkute
---

# Configure managed rules in Web Application Firewall

When you enable the [Web Application Firewall (WAF)](web-application-firewall.md) for your Power Pages site, a subset of Azure managed rules relevant to Power Pages are turned on by default. For more information on rules and rule groups, see [Web Application Firewall DRS rule groups and rules](/azure/web-application-firewall/afds/waf-front-door-drs?tabs=bot#bot).

## Prerequisites 

- You must be an admin to configure custom rules.
- [Web Application Firewall](web-application-firewall.md) must be enabled for the site.
- You can't configure Web Application Firewall managed rules in Government Community Cloud (GCC), Government Community Cloud (GCC High), Department of Defense (DoD), China, and the UAE region.

## Enable or disable managed rules in WAF for Power Pages sites

If your site has advanced customizations, certain rules can inadvertently block valid requests. Review the [WAF logs](/power-pages/security/web-application-firewall-logs) and  disable the required rules.

To enable or disable managed rules:

1. Navigate to the [Security workspace](/power-pages/getting-started/use-security-workspace).

1. Select **Web Application Firewall**.

1. On the right, select the **Managed rules** tab.

1. To disable a rule, select it and then select **Disable**.

1. To enable a specific managed rule that's currently disabled, select **Add new rule**, choose **Managed**, and select the rule you want to enable.

1. Select **Save**.

## Configure bot protection rules

Bot protection rules help block requests that originate from automated bots. Bots are typically categorized as:

- Good bots, like search engine crawlers.
- Bad bots, like malicious scrapers and spam bots.
- Unknown bots, which don't identify themselves clearly.

When you enable bot protection rules, the system blocks requests that match these rules based on your configuration.

To configure bot protection rules:

1. Navigate to the [Security workspace](/power-pages/getting-started/use-security-workspace).

1. Select **Web Application Firewall**.

1. On the right, select the **Managed rules** tab.

1. Select **Add new rule**, and then select **Bot protection rules** (Good bots, Bad
   bots, or Unknown bots).

1. Select **Save**.

### See also

[Websites - Create Waf Rules using REST API](/rest/api/power-platform/powerpages/websites/create-waf-rules)
