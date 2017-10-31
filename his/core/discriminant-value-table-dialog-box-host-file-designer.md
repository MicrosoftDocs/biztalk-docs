---
title: "Discriminant Value Table Dialog Box (Host File Designer)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ebiz.his.2006.tidesigner.dialog.dvt.hostfiles"
ms.assetid: 51e5ff81-f0ae-4fda-b821-6787c45e9a8b
caps.latest.revision: 3
---
# Discriminant Value Table Dialog Box (Host File Designer)
Use the **Discriminant Value Table** dialog box to create the logic for determining which union member returns information to the calling procedure. You can open the **Discriminant Value Table** dialog box by viewing the properties of an instanced union member, clicking **DVT**, and then clicking the ellipsis (**…**) button.  
  
|Use this|To do this|  
|--------------|----------------|  
|Discriminant Variable|List the name of the selected union.|  
|Discriminant type|List the data type that the union will use to create the logic.|  
|Discriminant Value Table|Create the Discriminant Value Table. The **Union Member** column lists the union members that will be checked, in order. The **Condition** column describes what to check for in order to use that member.|  
|Move Up|Move a union member and associated condition up in priority.|  
|Move Down|Move a union member and associated condition down in priority.|  
|Delete|Delete a union member and associated condition from the DVT. It does not delete the member from the union. You may add the union member back into the DVT at any time.|  
|OK|Save the additions you make to the DVT, and close the dialog box.|  
|Cancel|Close the dialog box without saving the changes you made to the DVT.|  
  
## See Also  
 [Host Files Designer](../core/host-files-designer.md)