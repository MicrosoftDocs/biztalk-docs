---
description: "Learn more about: Resolving Data Loss of In-Progress Orchestrations"
title: "Resolving Data Loss of In-Progress Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Resolving Data Loss of In-Progress Orchestrations
MessageBox databases contain the state of orchestrations that are currently in progress. Although there is no way to tell exactly what data has been lost from the MessageBox databases, there are some steps you can take to gather information about the lost data:  
  
-   Determine what messages have been sent and received in the current orchestrations, and what external systems have been used after the point of recovery. For example, if your system maintains an external log of messages and events, you can examine that log. You may also need to manually review the external systems to see what activities have occurred.  
  
-   After you determine the cause of the data loss, you can begin to correct the restored system, deciding which processes can continue, which processes must be terminated and restarted (by resubmitting the lost activation messages), and which processes have completed successfully and can be terminated. This process depends largely on the architecture of your system and must be considered as part of your system recovery planning.  
  
## See Also  
 [Resolving Data Loss](../core/resolving-data-loss.md)
