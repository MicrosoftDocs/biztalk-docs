---
description: "Learn more about: Communication between OrderBroker and OrderManager"
title: "Communication between OrderBroker and OrderManager | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, publishing [MessageBox database]"
  - "MessageBox database, publishing"
ms.assetid: 1b77dcd2-f7a5-4013-b9a2-c06ace161792
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Communication between OrderBroker and OrderManager
The order broker and the order manager orchestrations (**OrderBroker**, **OrderManager**) communicate through the MessageBox database rather than being direct partner bound. This ensures that the broker and manager are loosely coupled so that they can, if necessary, be located in separate BizTalk groups and in geographically-separated locations. Separating the orchestrations this way requires only administrative configuration and does not require any code changes.  
  
 In the solution as presently configured, the order broker marks messages for a particular order manager and sends them to the MessageBox. In turn, the order manager filters for messages intended for it and takes those messages from the MessageBox. This indirection—communicating through the MessageBox rather than direct binding—makes it easy to move the broker and manager to separate groups.  
  
 If there are different groups responsible for maintaining the broker and manager or if they need to be in geographically separate locations, the design makes it easy to accommodate this. All you need to do is move the orchestrations to different BizTalk groups. After the orchestrations are in separate groups, reconnecting them only requires creating ports. In the order broker group, you must create a send port that has the same filter as the order manager, but that forwards the message to the new group. In the order manager group, you must create a receive port that receives the message and puts it in the MessageBox database.  
  
 You can move the applications by exporting them to create MSI files, one each for the broker and manager. For more information about exporting applications, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)
