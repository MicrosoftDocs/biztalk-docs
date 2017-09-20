---
title: "Keyboard Shortcuts Specific to the Port Surfaces | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "keyboard shortcuts, Orchestration Designer"
  - "Orchestration Designer, keyboard shortcuts"
ms.assetid: 42c6fd89-c32a-4cb5-a1a5-47cc87b680a9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Keyboard Shortcuts Specific to the Port Surfaces
The following keys are active in the left and right Port Surfaces.  
  
|Key|Effect|  
|---------|------------|  
|DOWN ARROW|If a Role Link has the focus, focus shifts to the first port inside it. If there are no ports inside the Role Link, focus shifts to the next port or Role Link below it.<br /><br /> If a port has the focus, focus shifts to the next port or operation below it.<br /><br /> If an operation has the focus, focus shifts to its first operation part. For the \<New Operation> template, focus shifts to the next port.<br /><br /> If an operation part has the focus, focus shifts to the next operation part, operation, or port below it.<br /><br /> There is no effect if no more objects exist below the current one.|  
|UP ARROW|Same as the DOWN key, but in the opposite direction.<br /><br /> There is no effect if no more objects exist above the current one.|  
|RIGHT ARROW|Left Port Surface:<br /><br /> -   If an operation part has the focus, focus goes to the first port connector leading out of it. If there are no connections on the current operation part, pressing this key has no effect.<br />-   If an operation has the focus, focus goes to the first port connector of the operation's first part that has a connection. If there are no connections on the operation, pressing this key has no effect.<br />-   If a port connector gets the focus, whatever was selected in the Port Surface receives inactive selection.<br /><br /> Right Port Surface:<br /><br /> -   No effect.|  
|LEFT ARROW|Same as the RIGHT ARROW key, except in the opposite directions (that is, no effect for the left Port Surface, and the focus can go onto a port connector for the right Port Surface).|  
|HOME|Focus and selection shifts to the first shape in the channel.|  
|END|Focus and selection shifts to the last shape in the channel.|  
  
## See Also  
 [Orchestration Designer Keyboard Shortcuts](../core/orchestration-designer-keyboard-shortcuts.md)