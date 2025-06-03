---
description: "Learn more about: What is Event Tracking?"
title: "What is Event Tracking?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# What is Event Tracking?
Tracked message event data is based upon events (for example, when a service begins or ends, or when a message is sent or received). The message event tracking process returns a list of the events that have occurred, enabling you to see everything that happened based on the tracking filters you have set.  
  
 You can track the start and end of orchestrations and ports, when messages are sent and received, as well as the execution of each shape in an orchestration.  
  
 The BizTalk Tracking (BizTalkDTADb) database contains a DTA_Services audit table. This table contains history of all deployed services—pipelines, transports, and orchestrations. It does not keep track of undeployments.  
  
 You can track the contents of a message as well as the promoted properties of a message. Tracking message events defines these actions as **Message Body** tracking and **Message Property** tracking. Although envelopes appear in the message event tracking output, you cannot track message properties from them.  
  
## See Also  
 [Manage and Track BizTalk Server artifacts](managing-artifacts.md)
