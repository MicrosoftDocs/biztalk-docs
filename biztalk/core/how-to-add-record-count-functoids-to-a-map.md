---
description: "Learn more about: How to Add Record Count Functoids to a Map"
title: "How to Add Record Count Functoids to a Map"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add Record Count Functoids to a Map
The **Record Count** functoid enables you to generate a count of the number of times a record occurs in an instance message.  
  
 For conceptual information about the **Record Count** functoid, see [Record Count Functoid](../core/record-count-functoid.md).  
  
### To add the Record Count functoid to a map and configure it  
  
1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.  
  
    The list of advanced functoids in the chosen category appears.  
  
2. Drag the **Record Count** functoid (![Image that represents the Record Count functoid.](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) from the Toolbox to the appropriate location on a grid page.  
  
   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display the other grid page first.  
  
   > [!NOTE]
   >  If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  
  
3. To establish the input parameter for the **Record Count** functoid, create an input link by dragging a looping record from the source schema to the **Record Count** functoid, or dragging the **Record Count** functoid to a looping record in the source schema.  
  
4. To use the output parameter from the **Record Count** functoid, create an output link by dragging the **Record Count** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Record Count** functoid.  
  
   > [!NOTE]
   >  As with other functoids, the output of the **Record Count** functoid can be used as input to another functoid.  
  
## See Also  
 [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)
