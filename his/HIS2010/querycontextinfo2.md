---
title: "QueryContextInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2674a112-e88c-422f-a869-db98b75473aa
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
 [ClearAllContext](../HIS2010/clearallcontext2.md)   
 [ClosePersistentConnection](../HIS2010/closepersistentconnection2.md)   
 [CountContext](../HIS2010/countcontext2.md)   
 [DeleteContext](../HIS2010/deletecontext1.md)   
 [GetConnectionInfo](../HIS2010/getconnectioninfo1.md)   
 [ReadContext](../HIS2010/readcontext2.md)   
 [UpdateContextInfo](../HIS2010/updatecontextinfo2.md)   
 [WriteContext](../HIS2010/writecontext2.md)   
 [Persistent Connections](../HIS2010/persistent-connections1.md)