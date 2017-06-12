---
title: "IBaseMessageContext Interface (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b67fc3aa-4326-4c45-af54-a8e24553fc66
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext Interface (COM)
Provides access to the properties of the message and allows promotion of the properties.  
  
 For a list of all members of this type, see [IBaseMessageContext Members](../core/ibasemessagecontext-members-com.md).  
  
> [!NOTE]
>  For information on using this interface within managed code, see the `IBaseMessageContext Interface`.  
  
## Remarks  
 This interface encapsulates the message context, which is essentially a property bag for storing object properties. The context object is contained within the message.  
  
 Notice that existing properties never have a NULL value. A NULL value means that the property does not exist. For example:  
  
-   Attempting to set (or promote) a property value to NULL deletes the property with S_OK.  
  
-   Attempting to read a nonexistent property returns NULL with S_OK.  
  
-   For predicate-related interfaces, "x:a=NULL" (VT_NULL), which is the same as the hypothetical NotExists(x:a) predicate, is the test for nonexistence of a property x:a.  
  
 Multivalued property values are still contained in the same single variant value (pVar).  
  
  
## See Also  
 [IBaseMessageContext Members (COM)](../core/ibasemessagecontext-members-com.md)