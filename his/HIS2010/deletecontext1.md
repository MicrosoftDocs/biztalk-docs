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
 [ClearAllContext](../HIS2010/clearallcontext2.md)   
 [ClosePersistentConnection](../HIS2010/closepersistentconnection2.md)   
 [CountContext](../HIS2010/countcontext2.md)   
 [GetConnectionInfo](../HIS2010/getconnectioninfo1.md)   
 [QueryContextInfo](../HIS2010/querycontextinfo2.md)   
 [ReadContext](../HIS2010/readcontext2.md)   
 [UpdateContextInfo](../HIS2010/updatecontextinfo2.md)   
 [WriteContext](../HIS2010/writecontext2.md)   
 [Persistent Connections](../HIS2010/persistent-connections1.md)