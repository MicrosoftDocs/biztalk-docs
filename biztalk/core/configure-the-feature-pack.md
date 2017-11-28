---
title: "Configure the feature pack | Microsoft Docs"
description: Install and configure feature pack 1, and feature pack 2. See the new features list, including API Management, team services deployment, new Azure adapters, backups, and more in BizTalk Server 2016 
ms.custom: ""
ms.date: "11/22/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1027bfa6-49b9-4f58-a2e2-3e0ae2fc3bf3
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the feature pack

## Overview

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] uses feature packs to provide improvements, features, and closer integration with Azure. These feature packs extend functionality in key areas, such as deployment, security, analytics, runtime, and backup. 

> [!NOTE]
> The feature packs are available with the Enterprise and Developer editions of [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] when: 
> 
> - Used with Software Assurance (SA), OR
> - Running [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in Azure using an Enterprise Agreement
> 
> The feature packs are not available for any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] edition, or any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version. 

## Download and install

The feature packs are cumulative. So when you install feature pack 2, you also get the features and updates in feature pack 1.

* Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).

* Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).

#### Install

1. Run setup as administrator.
2. In **Welcome**, select **Next**. 
3. Accept the license agreement, and select **Next**. 
4. Continue with the installation. During the install, several command windows may open and close. When complete, you are prompted to **Finish**.

A setup log is created in `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.

>[!TIP]
> For comprehensive guidance on the installation, see the [Feature Pack step-by-step installation](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/) blog post.

## Feature Pack 2 updates

#### [Expose SOAP endpoints with API Management](../core/connect-to-azure-api-management.md)

Expanding on the API management integration made with Feature Pack 1, you can now expose a WCF-BasicHTTP receive location as a SOAP endpoint using the BizTalk Server Administration console. 

#### [Use the Event Hub adapter](event-hubs-adapter.md)

Send messages from BizTalk to Azure Event Hubs, and receive messages from Azure Event Hubs to BizTalk Server. When you configure the transport properties, you can easily sign in to your Azure account, and automatically select your Azure Event Hubs namespace, and Event Hub.

#### [Backup to Azure blob account](../core/how-to-configure-the-backup-biztalk-server-job.md)
The Backup BizTalk Server job backs up the BizTalk databases and log files. When you configure this SQL Agent job, you can enter an Azure blob storage account within the job properties. This gives you another option to backup your data, instead of using a local physical disk. 

#### [Multi-machine deployment using VSTS](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
Using deployment groups, you can deploy your applications to multiple BizTalk Servers. You can also set the application name within the application project, and install your application by entering your management server.

[Deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) provides more details on how this is done in VSTS.  

#### [Use Service Bus Premium](../core/sb-messaging-adapter.md)

The Service Bus adapter supports Service Bus Premium, including sending messages to partitioned queues and topics. [Service Bus Premium and Standard messaging tiers](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging) details more about Service Bus Premium. 

#### [Use named instances with Application Insights](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
When you enable Analytics, and enter the Application Insights key, you may get error: 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

This happens when you use SQL named instances. This is fixed in this feature pack; you can use SQL default instances, and SQL named instances. 

#### TLS 1.2 support

TLS 1.2 is fully supported in BizTalk Server, including all the adapters and all the accelerators. You can disable SSL, TLS 1.0, and TLS 1.1 on the BizTalk Server. 

Key information: 

* Any external systems communicating with BizTalk also need to support TLS 1.2
* Any custom code, such as functoids, may need to be updated to support TLS 1.2

[Description of the TLS/SSL protocol](https://support.microsoft.com/kb/3155464) describes how to setup a TLS 1.2 environment. 

#### Use latest Newtonsoft JSON 
Newtonsoft is a JSON framework for .NET. In this feature pack, support for version 10.0.3 is included. [Download v. 10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3) directly from NuGet. 


## Feature Pack 1 updates

#### [Send tracking data to Application Insights](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

Send tracking data to Azure Application Insights to use its features, such as analytics, machine learning, diagnostics, and more. 

#### [Configure the operational data feed using Power BI](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

Send tracking data to Power BI using oData. For example, get a visual representation of your tracking data from your ports and orchestrations. 

#### [Connect to the management REST APIs in BizTalk](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

Use REST APIs to remotely manage your BizTalk artifacts, including agreements, suspended instances, unenlisted orchestrations, and more.

#### [Configure advanced scheduling](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

Enable advanced scheduling in your receive locations. For example, set the timezone, or set a recurrence service window for a specific day on a specific month.

#### [Configure automatic deployments with VSTS](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

Use Visual Studio Team Services (VSTS) to automatically deploy your solutions, or update existing applications. VSTS communicates with an agent installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

#### [Connect to SQL Server Always Encrypted columns with BizTalk Server](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

Use the WCF-SQL adapter to query encrypted columns from an Always Encrypted database in SQL Server.

#### [Integrate with API Management](../core/connect-to-azure-api-management.md)

Within your Azure API management service, you can create and expose an API as WSDL, and use the URI to a BizTalk SOAP endpoint.  