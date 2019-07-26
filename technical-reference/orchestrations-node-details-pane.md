---
title: Orchestrations Node, Details Pane
TOCTitle: Orchestrations Node, Details Pane
ms:assetid: 83a5b192-66b6-4c54-a67b-85b949d449b3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561136(v=BTS.80)
ms:contentKeyID: 51529358
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.resultsobject.orchestration
---

# Orchestrations Node, Details Pane

 

Use the Orchestrations node details pane to control and manage orchestrations in the application. Right-click a specific orchestration to display the following commands:

  - **Start**. Starts the orchestration and allows messages to be routed to it.

  - **Stop**. Stops the activation subscriptions. Messages routed to this orchestration are suspended (resumable).

  - **Enlist**. When the orchestration is in a Bound state, **Enlist** sets the activation subscriptions to Stopped. Messages routed to this orchestration are suspended (resumable).

  - **Un-enlist**. Disables the activation subscriptions so that no new instances can be created, but processes already begun are completed.

  - **Remove**. Removes the selected orchestration from the application and undeploys the assembly that contains it and the other components of that assembly. The application must be stopped before you can remove the orchestration.

  - **Move To Application**. Displays the **Move to Application** dialog box, which you use to move artifacts from the current application in the Administrative Console to a different application.

  - **Tracking**. Displays the **Orchestration Tracking Options** window. This window is identical to the **Tracking** tab in the **Orchestration Properties** window. You can use this window to set tracking options for orchestration events.

  - **Properties**. Displays the **Orchestration Properties** window.

## See Also

[About Orchestrations](https://msdn.microsoft.com/library/aa578451\(v=bts.80\))  
[Creating Orchestrations](https://msdn.microsoft.com/library/aa577489\(v=bts.80\))  
[How to Enlist an Orchestration](https://msdn.microsoft.com/library/aa578153\(v=bts.80\))

