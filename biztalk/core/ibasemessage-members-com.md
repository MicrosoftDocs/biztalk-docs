---
title: "IBaseMessage Members (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bf31a14-56e0-4ba1-ba55-033e34735ad5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage Members (COM)
[IBaseMessage overview](../core/ibasemessage-interface-com.md)  
  
## Public Properties  
  
|||  
|-|-|  
|![](../core/media/pubproperty.gif "pubproperty") [BodyPart](../core/ibasemessage-bodypart-property-com.md)|Gets the body part, or main part, of the message.|  
|![](../core/media/pubproperty.gif "pubproperty") [BodyPartName](../core/ibasemessage-bodypartname-property-com.md)|Gets the name of the body part, or main part, of the message.|  
|![](../core/media/pubproperty.gif "pubproperty") [Context](../core/ibasemessage-context-property-com.md)|Represents the message context.|  
|![](../core/media/pubproperty.gif "pubproperty") [IsMutable](../core/ibasemessage-ismutable-property-com.md)|Gets a value indicating whether the message context can be changed by components during processing.|  
|![](../core/media/pubproperty.gif "pubproperty") [MessageID](../core/ibasemessage-messageid-property-com.md)|Gets the unique message ID for the message and binds all the message parts together.|  
|![](../core/media/pubproperty.gif "pubproperty") [PartCount](../core/ibasemessage-partcount-property-com.md)|Gets the total number of parts in the message.|  
  
## Public Methods  
  
|||  
|-|-|  
|![](../core/media/pubmethod.gif "pubmethod") [AddPart](../core/ibasemessage-addpart-method-com.md)|Adds a part to the message.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetErrorInfo](../core/ibasemessage-geterrorinfo-method-com.md)|Gets the exception that caused the error.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetPart](../core/ibasemessage-getpart-method-com.md)|Accesses the message parts.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetPartByIndex](../core/ibasemessage-getpartbyindex-method-com.md)|Retrieves a part and its name by supplying the part index.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetSize](../core/ibasemessage-getsize-method-com.md)|Gets the size of the message.|  
|![](../core/media/pubmethod.gif "pubmethod") [RemovePart](../core/ibasemessage-removepart-method-com.md)|Removes a part from the message.|  
|![](../core/media/pubmethod.gif "pubmethod") [SetErrorInfo](../core/ibasemessage-seterrorinfo-method-com.md)|Sets the error information.|  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)