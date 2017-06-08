---
title: "IProbeMessage Interface (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3683382-1ac3-493e-8bf7-96fa7ec0722c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IProbeMessage Interface (COM)
Defines the methods and properties for components that need probing functionality.  
  
 For a list of all members of this type, see [IProbeMessage Members (COM)](../core/iprobemessage-members-com.md).  
  
> [!NOTE]
>  For information on using this interface within managed code, see the `IProbeMessage Interface`.  
  
## Remarks  
 All components included in a stage configured for **FirstMatch** execution need to implement this interface before the messaging component checks to see if the message is recognizable. This behavior is used when several parser components are placed in one pipeline. The first parser that can recognize the message format is executed.  
  

## See Also  
 [IProbeMessage Members (COM)](../core/iprobemessage-members-com.md)