---
title: "ClearAllContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c92a21a8-1313-4767-8d30-ccfbb03f07b9
caps.latest.revision: 3
---
# ClearAllContext
Use the **ClearAllContext** method to remove all the entries in a TI Context array.  
  
## Syntax  
  
```  
  
HRESULT ClearAllContext (  
```  
  
#### Parameters  
 *prgContextArray*  
 This SAFEARRAY parameter contains the TI Context that is to be cleared.  
  
## Return Codes  
 S_OK  
 The method call completed successfully.  
  
 E_INVALIDARG  
 One or more of the parameters passed are invalid.  
  
 E_FAIL  
 An internal processing error occurred.  
  
## See Also  
 [ClosePersistentConnection](../core/closepersistentconnection2.md)   
 [CountContext](../core/countcontext2.md)   
 [DeleteContext](../core/deletecontext1.md)   
 [GetConnectionInfo](../core/getconnectioninfo1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [ReadContext](../core/readcontext2.md)   
 [UpdateContextInfo](../core/updatecontextinfo2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Persistent Connections](../core/persistent-connections1.md)