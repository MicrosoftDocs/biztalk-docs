---
title: "Discriminant Value Table Dialog Box1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c49d2d4-1fe4-48fa-86f2-27492c26dc55
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Discriminant Value Table Dialog Box
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
 [Host Integration Server Designer UI](../core/host-integration-server-designer-ui1.md)