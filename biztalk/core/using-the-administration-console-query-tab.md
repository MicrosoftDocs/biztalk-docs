---
title: "Using the Administration Console Query Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Administration Console [BizTalk Server], Query tab"
  - "Query tab [Administration Console]"
ms.assetid: 7655f0b6-9217-46c4-88e0-ca2e661ce7a6
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Administration Console Query Tab
You can use the Query tab on the Group Hub page in the BizTalk Server Administration Console to search for and locate specific running and suspended service instances, messages, or subscriptions. Queries performed using the Administration Console locate live items, which are stored in the MessageBox database. A new query tab appears each time you run a new query.  
  
 To locate tracked or archived messages or service instances, you use message event and service instance tracking. For more information, see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).  
  
> [!NOTE]
>  When you execute a query for service instances, the result set that is returned will display a value of **\<Name is not available>** for the **ServiceName** field of a service instance if the corresponding send port, receive location, or orchestration has been deleted.  The **ServiceName** field of a service instance is populated by a lookup into the BizTalk management database for the friendly name of the send port, receive location, or orchestration.  If the send port, receive location, or orchestration is deleted then the lookup for the friendly name fails and **\<Name is not available>** is displayed.  
  
## In This Section  
  
-   [How to Open a Saved Query](../core/how-to-open-a-saved-query.md)  
  
-   [How to Search for All Service Instances](../core/how-to-search-for-all-service-instances.md)  
  
-   [How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md)  
  
-   [How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md)  
  
-   [How to Search for Messages](../core/how-to-search-for-messages.md)  
  
-   [How to Search for Subscriptions](../core/how-to-search-for-subscriptions.md)  
  
-   [How to Save a Query](../core/how-to-save-a-query.md)  
  
-   [How to Search for Tracked Message Events](../core/how-to-search-for-tracked-message-events.md)  
  
-   [How to Search for Tracked Service Instances](../core/how-to-search-for-tracked-service-instances.md)