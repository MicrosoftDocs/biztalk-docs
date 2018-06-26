---
title: "How to Add Parameters to Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, parameters"
ms.assetid: 35c731ed-6327-4de7-8d2e-4d14024bda77
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Parameters to Orchestrations
You can specify what parameters your orchestration should take in the Orchestration View window. An orchestration can take the following items as parameters:  
  
- Messages  
  
- Variables (including objects)  
  
- Correlation sets  
  
- Role links  
  
- Ports  
  
  Parameters can be passed between orchestrations as in parameters or out parameters. In parameters can be passed by value or by reference. Out parameters can only be passed by reference. Parameters can include variables, messages, correlation sets, role links, and ports.  
  
### To set orchestration parameters  
  
1.  In the Orchestration View window, use the **Orchestration Parameters** folder to add variables, messages, and ports.  
  
2.  For each item added to the **Orchestration Parameters** folder, use the Properties window to specify the **Direction** property:  
  
    -   In—A parameter passed in by value.  
  
    -   Ref—A parameter passed in by reference.  
  
    -   Out—A parameter passed out by reference.  
  
### To add a parameter to an orchestration  
  
1. In the Orchestration View window, right-click the **Orchestration Parameters** folder and then click the kind of parameter you want.  
  
2. For configured ports and role links, use the wizard to configure the parameter.  
  
    —Or—  
  
    For other parameter types, use the properties page to configure the parameter.  
  
   **Parameter types**  
  
   Parameters can be passed by value, as reference parameters, and as out parameters. When a parameter is passed by value to an orchestration, a copy of the data is made and used by the orchestration.  
  
   When you use a reference parameter, no copy is made. The memory location that contains the data is shared between the calling program and the orchestration, and the contents of this memory location can be modified by the orchestration. Such a modification means that the value of the parameter is changed not only in the orchestration, but also in the calling program.  
  
   An out parameter is similar to a reference parameter, but the orchestration cannot assume that it contains valid data when passed in; rather, the calling program expects the orchestration to assign a value to this parameter.  
  
   **Rules for orchestration parameters**  
  
-   You can pass only messages and variables (including objects) as out or reference parameters.  
  
-   You cannot pass out or reference parameters to an orchestration in a **Start Orchestration** shape.  
  
-   In parameters, including any role links and dynamic ports, must be definitely assigned before being passed to an orchestration.  
  
## See Also  
 [Orchestration Shapes](../core/orchestration-shapes.md)   
 [How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md)   
 [How to Use the Select Artifact Type Dialog Box](../core/how-to-use-the-select-artifact-type-dialog-box.md)