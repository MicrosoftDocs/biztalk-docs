---
title: "CountContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19eef6af-808f-4e96-83b7-90d92bafbdda
caps.latest.revision: 3
---
# CountContext
Use the **CountContext** method to acquire a count of the entries in a TI Context array.  
  
## Syntax  
  
```  
  
HRESULT CountContext (  
```  
  
#### Parameters  
 *prgContextArray*  
 This SAFEARRAY parameter contains TI Context entries that are passed to and returned from COM+ objects.  
  
 *pulContextEntriesCount*  
 Upon successful completion of the call, this integer parameter contains a count of the number of entries in the specified TI Context array.  
  
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
 [DeleteContext](../core/deletecontext1.md)   
 [GetConnectionInfo](../core/getconnectioninfo1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [ReadContext](../core/readcontext2.md)   
 [UpdateContextInfo](../core/updatecontextinfo2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Persistent Connections](../core/persistent-connections1.md)