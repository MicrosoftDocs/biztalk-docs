---
title: "Configure the feature pack | Microsoft Docs"
description: Install and configure feature pack 1, and feature pack 2. See the new features list, including API Management, team services deployment, new Azure adapters, backups, and more in BizTalk Server 2016 
ms.custom: ""
ms.date: "01/10/2020"
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

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] uses feature packs to provide improvements, features, and closer integration with Azure. These feature packs extend functionality in key areas, such as deployment, security, analytics, runtime, maintainance, standard compliance, and hybrid integration. 

> [!NOTE]
> The feature packs are available with the Enterprise and Developer editions of [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] when: 
> 
> - Used with Software Assurance (SA), OR
> - Running [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in Azure using an Enterprise Agreement
> 
> The feature packs are not available for any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] edition (Standard and Branch editions), or any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version (2013 R2, 2013, 2010, and so on). 

## Download and install

The feature packs are cumulative. So when you install feature pack 3, you also get the features and updates in feature packs 2 and 1. You also get the latest cumulative updates.

* Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 3 CU6](https://aka.ms/bts2016fp3).

* Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).

* Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).

#### Install

1. Run setup as administrator.
2. In **Welcome**, select **Next**. 
3. Accept the license agreement, and select **Next**. 
4. Continue with the installation. During the install, several command windows may open and close. When complete, you are prompted to **Finish**.

A setup log is created in `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.

>[!TIP]
> For comprehensive guidance on the installation, see the [BizTalk Server 2016 Feature Pack 3: step-by-step installation](https://blog.sandro-pereira.com/2018/06/26/biztalk-server-2016-feature-pack-3/) blog post.

## Feature Pack 3 updates

**Office 365 Adapters**

Microsoft Office 365 is a cloud-based subscription service that brings together the best tools for the way people work today. By combining best-in-class apps like Excel and Outlook with powerful cloud services like OneDrive and Microsoft Teams, Office 365 lets anyone create and share anywhere on any device.

Microsoft BizTalk Server adapters for Office 365 enable IT professionals and enterprise developers to integrate Outlook mail, contacts, and schedules with new solutions based on BizTalk Server 2016.

#### [Office 365 Mail adapter](office365-mail-adapter.md)
Using the BizTalk Adapter for Office 365 Mail, you can read, mark as read or delete Outlook e-mail messages through one-way BizTalk Server receive locations. Using this adapter, you can write e-mail message, including setting message priority, through one-way static or dynamic BizTalk Server send ports.

#### [Office 365 Calendar adapter](office365-calendar-adapter.md)
Using the BizTalk Adapter for Office 365 Calendar, you can get future calendar events through one-way BizTalk Server receive locations. Using this adapter, you can create calendar events, and enter required and optional attendees, through one-way static or dynamic BizTalk Server send ports.

#### [Office 365 Contact adapter](office365-contact-adapter.md)
Using the BizTalk Adapter for Office 365 Contact, you can create contacts, and enter all settings, through one-way static or dynamic BizTalk Server send ports.

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

#### [Send tracking data to Azure Event Hubs](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
Expanding on the Feature Pack 1 capabilities, you can now send your tracking data to Azure Event Hubs. Support for SQL names instances has also been added.

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

Send tracking data to Application Insights to use its features, such as analytics, machine learning, diagnostics, and more. 

#### [Configure the operational data feed using Power BI](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

Use OData visualization tools like PowerBI to query operational data. For example, get a visual representation of your tracking data from your ports and orchestrations.

#### [Connect to the management REST APIs in BizTalk](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

Use REST APIs to remotely manage your BizTalk artifacts, including agreements, suspended instances, unenlisted orchestrations, and more.

#### [Configure advanced scheduling](../core/how-to-configure-scheduling-for-a-receive-location.md)

Enable advanced scheduling in your receive locations. For example, set the timezone, or set a recurrence service window for a specific day on a specific month.

#### [Configure automatic deployments with VSTS](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

Use Visual Studio Team Services (VSTS) to automatically deploy your solutions, or update existing applications. VSTS communicates with an agent installed on the BizTalk Server.

#### [Connect to SQL Server Always Encrypted columns with BizTalk Server](../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md)  

Use the WCF-SQL adapter to query encrypted columns from an Always Encrypted database in SQL Server.

#### [Integrate with API Management](../core/connect-to-azure-api-management.md)

Within your Azure API management service, you can create and expose an API as WSDL, and use the URI to a BizTalk SOAP endpoint.  

## Uninstall the feature pack

To uninstall the feature pack, be sure you're signed in as an administrator. Otherwise, the uninstall may not complete successfully, and the BizTalk Server project templates in Visual Studio may be removed.
