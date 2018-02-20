---
title: "Creating an Object View1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0ca522f-c18c-4f28-a3f9-f97e7e3d1d1a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Creating an Object View
Object views in host-initiated processing (HIP) provide different ways to view and manage Windows Server objects in the HIP environment. During the definition of an object view, all methods or a subset of the Objects methods can be defined in the view. This helps provide a level of security by limiting the number of methods available for execution.  
  
 When a host environment (HE) is associated with an object view, the level of security is elevated. With the HE association, only certain hosts can execute specific methods of an Object.  
  
 When the object view is finally associated with a local environment, the security is enhanced further by restricting the execution of a method on an object to a request from a specific host that made a request to a specific transport endpoint on the Windows operating system.  
  
 You can create new object views by using the **New Object View Wizard**. This wizard helps you construct the following administrative entities:  
  
-   A view of an object.  
  
-   One or more methods in the object to be defined on the view.  
  
-   A local environment association.  
  
-   Host environment association.  
  
-   Method resolution information.  
  
## See Also  
 [Working with Host-Initiated Processing](../core/working-with-host-initiated-processing1.md)