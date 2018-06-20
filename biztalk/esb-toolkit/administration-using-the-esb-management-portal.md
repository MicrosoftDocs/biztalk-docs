---
title: "Administration Using the ESB Management Portal | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 478d1dcc-e9b2-443b-be98-5b7545322401
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Administration Using the ESB Management Portal
The ESB Management Portal, included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], is a sample site that demonstrates the use of metrics and the possibilities that exist for extending the BizTalk ESB Toolkit. The portal provides a starting point from which you can build your own customized portal.  
  
 The ESB Management Portal is also a highly capable and useful tool that can help to maximize the use and efficiency of the ESB exception management system. In addition, the portal provides a user interface for an underlying Universal Description, Discovery, and Integration (UDDI) registry server and graphical configuration capabilities for features such as auditing, viewing history information, configuring alerts and notifications, and allowing users to subscribe to alerts that indicate faults occurring in ESB applications.  
  
 This section describes the common tasks you can accomplish using the ESB Management Portal, including the following:  
  
-   [Working with Exceptions and Fault Messages](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [Configuring Alerts, Notifications, and Subscriptions](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [Viewing and Managing Auditing and History](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [Analyzing Fault Trends Using Charts and Reports](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [Viewing and Publishing UDDI Registrations](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  For a detailed description of the individual features of the ESB Management Portal, see [ESB Management Portal Feature Reference](../esb-toolkit/esb-management-portal-feature-reference.md).  
  
## ESB Portal Technologies  
 The ESB Management Portal takes advantage of the following technologies:  
  
- [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
- ASP.NET
  
- [Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292)). The ESB Management Portal uses the following Enterprise Library assemblies:  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Caching**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Common**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Data**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Logging**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Validation**  
  
  -   Microsoft.Practices.Unity  
  
- [Microsoft Chart Controls](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293) for Microsoft .NET Framework 4  
  
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] metric tracking extends only to fault tracking for the exception management system.