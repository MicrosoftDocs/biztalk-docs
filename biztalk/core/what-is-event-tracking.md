---
title: "What is Event Tracking? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [HAT tracking], events"
  - "DTA_Services audit table [HAT]"
  - "HAT, events"
  - "events, tracking"
  - "tracking, events"
  - "Tracking database, DTA_Services audit table"
  - "events, HAT"
ms.assetid: dd211752-d1af-4287-967a-908b8d067ebb
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What is Event Tracking?
Tracked message event data is based upon events (for example, when a service begins or ends, or when a message is sent or received). The message event tracking process returns a list of the events that have occurred, enabling you to see everything that happened based on the tracking filters you have set.  
  
 You can track the start and end of orchestrations and ports, when messages are sent and received, as well as the execution of each shape in an orchestration.  
  
 The BizTalk Tracking (BizTalkDTADb) database contains a DTA_Services audit table. This table contains history of all deployed services—pipelines, transports, and orchestrations. It does not keep track of undeployments.  
  
 You can track the contents of a message as well as the promoted properties of a message. Tracking message events defines these actions as **Message Body** tracking and **Message Property** tracking. Although envelopes appear in the message event tracking output, you cannot track message properties from them.  
  
## See Also  
 [Configuring Tracking Using the BizTalk Server Administration Console](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)