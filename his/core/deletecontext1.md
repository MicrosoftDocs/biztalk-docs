---
title: "DeleteContext1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37a3b27c-23d0-4682-9f01-834ba3447d1e
caps.latest.revision: 3
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
 [ClearAllContext](../core/clearallcontext2.md)   
 [ClosePersistentConnection](../core/closepersistentconnection2.md)   
 [CountContext](../core/countcontext2.md)   
 [GetConnectionInfo](../core/getconnectioninfo1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [ReadContext](../core/readcontext2.md)   
 [UpdateContextInfo](../core/updatecontextinfo2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Persistent Connections](../core/persistent-connections1.md)