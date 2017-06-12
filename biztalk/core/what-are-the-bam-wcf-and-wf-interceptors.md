---
title: "What Are the BAM WCF and WF Interceptors? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 198bfdc9-86ff-4017-b65f-19616deeb9f4
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Are the BAM WCF and WF Interceptors?
Business Activity Monitoring (BAM) is a collection of tools, APIs, and services that allow you to manage aggregations, alerts, and profiles, and to instrument automated processes to send events to monitor relevant business metrics. Together, these provide end-to-end visibility into business processes and enable you to stay abreast of business process status and results.  
  
 BAM interceptors extend this same functionality into Windows Workflow Foundation (WF), Windows Communication Foundation (WCF), and other runtime environments. By using a BAM interceptor, you can track your business processes without recompiling your WF or WCF solution—integration is done through a configuration file.  
  
 By using the BAM WF or WCF interceptor in your project, you can:  
  
-   Use the BAM portal to view information about the business processes running in your WF or WCF application.  
  
-   Use BAM functionality without adding additional code to your application.  
  
-   Deploy your solution using familiar BizTalk Server tools and utilities.  
  
-   Leverage your existing BizTalk Server environment for existing and new WF and WCF applications.  
  
## Interceptor Components  
 At the core of each BAM interceptor is the Common Interceptor Foundation, a set of components that provide the foundation for building custom interceptors for heterogeneous environments. The Common Interceptor Foundation contains the following shared components:  
  
-   **bm.exe**, an enhanced version of the BAM deployment utility extended to modify interceptor configurations including add, remove, update, and list functionality.  
  
-   **CommonInterceptorConfiguration.xsd**, the Common Interceptor Foundation configuration XML schema. At minimum, all interceptor configurations must validate against this schema.  
  
## Windows Workflow Foundation (WF) Interceptor  
 The Windows Workflow Foundation interceptor enables you to transparently add BAM tracking functionality to new and existing WF applications. After the interceptor configuration has been deployed to the BAM Primary Import database and each instance of the WF application has been configured to load the BAM WF Interceptor, workflow data will be written to BAM with no additional code. The WF interceptor provides the following functionality:  
  
-   Plugs into existing WF applications without requiring code changes or recompilation.  
  
-   Enables run-time detection and support for changed configuration files. If a new version of an interceptor configuration file is detected, new workflow instances will use the new configuration while old workflow instances will complete using the old configuration.  
  
-   Supports transactions. The WF interceptor persists tracked items in a transactionally consistent way with WF transactions. Tracked items are only persisted when the WF transaction and the interceptor trasaction complete successfully.  
  
    > [!NOTE]
    >  The Windows Workflow interceptor does not support SharedConnectionWorkflowCommitWorkBatchService which uses the same SQL connection for both the tracking and persistence services.  
  
    > [!NOTE]
    >  In BizTalk Server, the Windows Workflow Foundation (WF) interceptor will not work with the new WF engine in .NET Framework 4. The WF interceptor will continue to work in .NET Framework 3.5 SP2.  
  
## Windows Communication Foundation (WCF) Interceptor  
 The Windows Communication Foundation interceptor provides BAM tracking functionality to your WCF applications. It provides the following functionality:  
  
-   Plugs into existing WCF applications without requiring code changes or recompilation.  
  
-   Tracks messages contained in WCF service calls.  
  
-   Tracks information from messages in WCF service calls.  
  
-   Participates in transactions flowed from the client or initiated internally for transacted service calls.