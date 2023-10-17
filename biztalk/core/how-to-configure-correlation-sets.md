---
description: "Learn more about: How to Configure Correlation Sets"
title: "How to Configure Correlation Sets"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure Correlation Sets
To configure your correlation set, you can select an existing correlation type, create a new correlation type, or modify an existing correlation type.  
  
### To assign a correlation type to a correlation set  
  
- Select an existing correlation type.  
  
   \- Or -  
  
   Right-click the new correlation type and select **Configure Correlation Properties**.  
  
   \- Or -  
  
   Click the Ellipsis (**...**) button on **Correlation** Properties in the **Properties** window.  
  
   The **Correlation Properties** dialog box comes up. Add properties that you want to include in your correlation set. If a correlation type was not already assigned to your correlation set, a new correlation type will be created.  
  
  If a correlation type already exists for your correlation set, and you add or remove properties with the **Correlation Properties** dialog box, the existing correlation type will be modified.  
  
#### To associate send and receive activities with a correlation set  
  
1.  Expand the **Correlation Set** node.  
  
2.  Select a send or receive activity from the drop-down.  
  
     \- Or -  
  
     Select the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to associate with the correlation set.  
  
#### To disassociate send and receive activities from a correlation set  
  
-   In the **Orchestration View** window, expand the correlation set node if necessary, right-click the activity you want to remove, and then click **Delete**.  
  
     \- Or -  
  
     Clear the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to disassociate from the correlation set.  
  
## See Also  
 [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md)   
 [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md)
