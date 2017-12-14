---
title: "DeleteContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d1cc8a7-2f7d-45fa-a0b8-fd12b5719ce2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DeleteContext
Use the **DeleteContext** method to remove an entry in a TI Context array.  
  
## Syntax  
  
```  
  
HRESULT DeleteContext (  
```  
  
#### Parameters  
 *bstrContextEntryNam*e  
 This string parameter contains the name of the TI Context entry to be removed.  
  
 *prgContextArray*  
 This SAFEARRAY parameter contains the TI Context entries that are passed to and returned from COM+ objects.  
  
## Return Codes  
 S_OK  
 The method call completed successfully.  
  
 E_INVALIDARG  
 One or more of the parameters passed are invalid.  
  
 E_FAIL  
 An internal processing error occurred.  
  
## See Also  
 [ClearAllContext](../core/clearallcontext1.md)   
 [ClosePersistentConnection](../core/closepersistentconnection1.md)   
 [CountContext](../core/countcontext1.md)   
 [GetConnectionInfo](../core/getconnectioninfo2.md)   
 [QueryContextInfo](../core/querycontextinfo1.md)   
 [ReadContext](../core/readcontext1.md)   
 [UpdateContextInfo](../core/updatecontextinfo1.md)   
 [WriteContext](../core/writecontext1.md)   
 [Persistent Connections](./persistent-connections2.md)