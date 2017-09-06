---
title: "How to Clean the Target Computer1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, removing"
  - "send ports, removing"
  - "cleaning target computer"
ms.assetid: 78986a33-3c77-48dc-88c4-b78f52911c22
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Clean the Target Computer
Deployment overwrites the receive location configuration. When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  
  
### To clean the target computer  
  
-   Remove send ports and receive locations bound to the orchestration.  
  
     If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
         For example, at a command prompt, run:  
  
         **cscript RemoveSendPort.vbs \<Send port name>**  
  
## See Also  
 [Deploying Ports and Assemblies](../core/deploying-ports-and-assemblies1.md)