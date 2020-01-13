---
title: "Operational Data Service | Microsoft Docs"
description: Operational Data Service 
ms.custom: "biztalk-2020"
ms.date: "01/07/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: "anneta"
---
# Operational Data Service

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, BizTalk Server provide the operational data service, which can be accessed or queried using OData visualization tools, like Power BI. [What is OData?](https://docs.microsoft.com/en-us/odata/overview)

## What is operational data
Operational data is information on the instances and messages flowing through your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment. The operational data feed is the same data you get looking at Group Hub in [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)].

The feed includes the following data tables:
* Application data
* AS2 Status Records
* Batching information
* Instance information
* Interchange Aggregations Records
* Interchange Status Records
* Messages
* Subscriptions
* Tracked Events
* Transaction reports
* Transaction sets

> [!TIP]
> [PowerBI.com](https://powerbi.microsoft.com) is a great resource to understand and learn more about Power BI.

## Prerequisites
* Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on any computer that has network access to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 
* [Configure the REST APIs](../install-and-config-guides/configure-biztalk-server.md) for **Operational data service**.
* Optional. Install and configure a [Power BI Gateway](https://powerbi.microsoft.com/gateway/) to connect [PowerBI.com](https://powerbi.microsoft.com) with your on-premises BizTalk Server. If you're not using an on-premises BizTalk Server, then you don't need the gateway.


## Use Power BI to Load Operational Data.

1. Download and install the [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on your BizTalk Server. You can select to open it, which is optional. If you have a work or school account, you may have access to Power BI. Try signing in with that account. Or, you can try it for free after signing up.
2. Open the `\Program Files (x86)\Microsoft BizTalk Server\OperationalDataService` folder, and open the `BizTalkOperationalData.pbit` file.

3. Power BI desktop opens, and you are prompted for a URL. Enter the `http://localhost/<yourWebSite>` URL that you created for your OData feed. For example, enter `http://localhost/BizTalkOperationalDataService`. Your URL looks similar to the following:
![Enter the URL](../core/media/operational-data-url.png)

4. Select **Load**. The window loads and connects to the different oData sources in the BizTalkOperationalDataService.json file. When it completes, the dashboard shows details about your environment.

## Couldn't authenticate
If you get `couldn't authenticate with the credentials provided` message similar to the following, then it’s possible your application pool identity doesn’t have enough access to the BizTalk Server databases. You can change the appPool identity within IIS to an account with more privileges, maybe your signed-in user account (which has local admin privileges).

![Couldn't authenticate with the credentials provided](../core/media/operational-data-authentication-error.png)

## Do more
This is just the beginning. Power BI also has a gateway that can be installed on an on-premises BizTalk Server. Using the gateway, you can publish your dashboard, get real-time data, and create a schedule to refresh the dashboard. The following blog does a great job detailing these steps:

* [How to publish BizTalk operational data on Power BI – Step-by-step configuration](https://blog.sandro-pereira.com/2017/05/07/biztalk-server-2016-feature-pack-1-how-to-publish-biztalk-operational-data-power-bi-step-by-step-configuration-part-3/)

The [Guided Learning](https://powerbi.microsoft.com/guided-learning/) is also a great place to learn more about Power BI, and all the things you can do.

## See also

[Learn more about Power BI](https://www.powerbi.com)
