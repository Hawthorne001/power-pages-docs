---
title: FAQ for configuring Web Application Firewall in Power Pages
description: Learn about frequently asked questions and answers to configure Web Application Firewall rules in Power Pages.
author: nageshbhat-msft
ms.topic: faq
ms.date: 05/28/2024
ms.author: nabha
ms.reviewer: kkendrick
contributors:
  - ProfessorKendrick
  - nageshbhat-msft
---

# FAQ for configuring Web Application Firewall in Power Pages

In this article, you'll learn about frequently asked questions related to configuring Web Application Firewall in Power Pages.

## I want to set up a WAF rule to ensure that my site only receives traffic from customers accessing it from the United States.

To configure WAF rule in this case, use the following rule settings:

| Parameter | Setting |
| - | - |
| Rule type | Match |
| Match type | Geo location |
| Country or region | United States |
| Traffic settings | Allow |

## My site receives an average of 1500 requests in 5 minutes. I want to configure a WAF rule to protect my site by preventing any DDoS attack. How should I set up my WAF rules?

Configure the rules with the following settings:

| Parameter | Setting |
| - | - |
| Rule name | Allow1500RequestsIn5Mins |
| Rule type | Rate limit |
| Rate limit in minutes | 5 minutes |
| Requests allowed within rate limit | 1500 |
| Match type | IP address |
| IP address or range | \* |
| Traffic settings | Deny |

## My site has been experiencing abnormal traffic for the past day. How can I analyze this traffic pattern and safeguard my site from potential attackers?

When you activate WAF for your site, all requests are logged and available for analysis. Download the WAF logs to examine the traffic patterns; these logs contain client IPs, socket IPs, and request URIs. You can then create custom rules using the IP address Match type to block identified IPs or ranges, or utilize Rate limit rules with specific URL parts to enforce regular threshold limits over one-minute intervals.