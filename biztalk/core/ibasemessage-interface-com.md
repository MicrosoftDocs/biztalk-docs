---
title: "IBaseMessage Interface (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c4ef1bc-a131-41c6-8a7d-3884c2a9c4b4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage Interface (COM)
Represents the basic composition of the message.  
  
 For a list of all members of this type, see [IBaseMessage Members](../core/ibasemessage-members-com.md).  
  
> [!NOTE]
>  For information on using this interface within managed code, see the `IBaseMessage Interface`.  
  
## Remarks  
 This interface must be implemented for messages that get published to the database and delivered to the orchestration. The component needs to use the [CreateMessage](../core/ibasemessagefactory-createmessage-method-com.md) method of the [IBaseMessageFactory](../core/ibasemessagefactory-interface-com.md) interface to create a new message object in memory.  
  
 
## See Also  
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)