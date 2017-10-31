---
title: "QueryContextInfo1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a8e9616-7857-4c82-a462-e872cfc4ff60
caps.latest.revision: 3
---
# QueryContextInfo
Use the **QueryContextInfo** method to acquire a count of the entries in a TI Context array, the names of the context entries, and the data types of the context entries.  
  
## Syntax  
  
```  
  
HRESULT QueryContextInfo (  
```  
  
#### Parameters  
 *prgContextArray*  
 This SAFEARRAY parameter contains the TI Context entries that are passed to and returned from COM+ objects.  
  
 *pulContextEntriesCount*  
 Upon successful completion of the call, this integer parameter contains a count of the entries in the specified TI Context array.  
  
 *prgContextNameArray*  
 This SAFEARRAY of strings parameter contains the TI Context entry names.  
  
 *prgContextTypeArray*  
 This SAFEARRAY of integers parameter contains the TI Context entry data types.  
  
## Return Codes  
 S_OK  
 The method call completed successfully.  
  
 E_INVALIDARG  
 One or more of the parameters passed are invalid.  
  
 E_FAIL  
 An internal processing error occurred.  
  
## See Also  
 [ClearAllContext](../core/clearallcontext.md)   
 [ClosePersistentConnection](../core/closepersistentconnection.md)   
 [CountContext](../core/countcontext.md)   
 [DeleteContext](../core/deletecontext.md)   
 [GetConnectionInfo](../core/getconnectioninfo.md)   
 [ReadContext](../core/readcontext.md)   
 [UpdateContextInfo](../core/updatecontextinfo.md)   
 [WriteContext](../core/writecontext.md)   
 [Persistent Connections](../Topic/Persistent%20Connections1.md)