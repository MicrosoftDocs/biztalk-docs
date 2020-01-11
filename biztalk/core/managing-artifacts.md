---
title: "Managing Artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], artifacts"
  - "managing [artifacts]"
  - "artifacts, managing"
  - "managing [artifacts], about managing artificats"
ms.assetid: aa7c5e60-7c16-4bcf-b913-b1bdfc5c7543
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Artifacts
This section describes how to manage artifacts, including how to add and remove them from a BizTalk application and how to configure their properties.  
  
 Artifacts are the items contained in a BizTalk application that are required for it to run. For background information about how artifacts are used in a BizTalk application, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md) For background information about artifacts, see [Runtime Architecture](../core/runtime-architecture.md). For information about how you manipulate artifacts when you create and modify a BizTalk application, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md).  

## Tracking artifacts
A big part of managing the artifacts you create is tracking. You can configure various tracking options during run time for orchestrations, send ports, receive ports, and pipelines using the BizTalk Server Administration console. You can change the tracking options for an item at any time, without interrupting the business process.

The tracking configuration settings allow you to track the following types of data:

- Inbound and/or outbound event data. For example, message ID, start and stop times for the artifact.

- Inbound and/or outbound message properties. For example, general and promoted properties for each message that the artifact processes.

- Inbound and/or outbound message bodies and parts. For example, body and parts for each message that the artifact processes.

- Orchestrations. Execution data for orchestration shapes.

[Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md) provides some good info. 


> [!TIP]
> If you set tracking options on a pipeline, then the tracking options are set globally for every port that uses the pipeline. This results in far more data being tracked than you may intend, and may impact system performance. During development, this may be normal. In production scenarios, we recommend you enable any tracking options on the send ports and receive ports, instead of the pipelines.
  
## In this section  

-   [Send tracking data to Azure](../core/send-tracking-data-to-azure.md)

-   [Configure the operational data feed using Power BI](../core/operational-data-service.md)
  
-   [Managing Orchestrations](../core/managing-orchestrations.md)  
  
-   [Managing Role Links](../core/managing-role-links.md)  
  
-   [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)  
  
-   [Managing Receive Ports](../core/managing-receive-ports.md)  
  
-   [Managing Receive Locations](../core/managing-receive-locations.md)  
  
-   [Managing Policies](../core/managing-policies.md)  
  
-   [Managing Schemas](../core/managing-schemas.md)  
  
-   [Managing Maps](../core/managing-maps.md)  
  
-   [Managing Pipelines](../core/managing-pipelines.md)  
  
-   [Managing Resources](../core/managing-resources.md)