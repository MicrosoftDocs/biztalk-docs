---
description: "Learn more about: Keyboard Shortcuts Specific to the Process Area"
title: "Keyboard Shortcuts Specific to the Process Area"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Keyboard Shortcuts Specific to the Process Area
The following table describes the keyboard navigation available in the Process Area, the central area of the design surface used to define the process flow of the orchestration.  
  
|Key|Effect|  
|---------|------------|  
|DOWN ARROW|Moves the selection to the next connecting line or shape below. If the shape is connected to several branches below (as in the case of a Decide shape), the selection moves to the first shape in the leftmost branch.<br /><br /> If selection is on the End shape for the orchestration, pressing this key has no effect, because there are no more shapes below it.|  
|UP ARROW|Moves the selection to the next connecting line or shape above. If the shape is connected to several branches above, selection moves to the last shape on the leftmost branch.<br /><br /> Pressing this key has no effect when the **Start** shape is selected.|  
|LEFT ARROW|If the selection is on a Send or Receive shape and the shape is connected to a port:<br /><br /> -   If the shape has a port connector leading to a port in the Left Port Surface, focus and selection shift to the port connector of the shape.<br />-   If the shape has a port connector leading to a port in the Right Port Surface, pressing this key has no effect.<br />-   If the shape has no port connector, navigation is the same as with any other shape.<br /><br /> For other shapes (or Send or Receive shapes not connected to a port):<br /><br /> -   If the selection is in a branch, and a branch exists with shapes on it to the left of the current branch, the selection moves to the nearest shape on the branch to the left.<br />-   The key has no effect anywhere else in the orchestration.|  
|RIGHT ARROW|Same as the LEFT ARROW key, but in the opposite direction.|  
|HOME|Selection changes to the connector that leads from the Start shape of the orchestration.|  
|END|Selection changes to the connector that leads into the End shape of the orchestration.|  
|NUM LOCK + -|Collapses the selected complex shape.|  
|NUM LOCK + +|Expands the selected complex shape.|  
|NUM LOCK + *|Expands the selected complex shape, plus any child complex shapes it may have.|  
  
## See Also  
 [Orchestration Designer Keyboard Shortcuts](../core/orchestration-designer-keyboard-shortcuts.md)
