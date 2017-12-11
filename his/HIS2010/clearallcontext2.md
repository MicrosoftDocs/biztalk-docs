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
 [ClosePersistentConnection](../HIS2010/closepersistentconnection2.md)   
 [CountContext](../HIS2010/countcontext2.md)   
 [DeleteContext](../HIS2010/deletecontext1.md)   
 [GetConnectionInfo](../HIS2010/getconnectioninfo1.md)   
 [QueryContextInfo](../HIS2010/querycontextinfo2.md)   
 [ReadContext](../HIS2010/readcontext2.md)   
 [UpdateContextInfo](../HIS2010/updatecontextinfo2.md)   
 [WriteContext](../HIS2010/writecontext2.md)   
 [Persistent Connections](../HIS2010/persistent-connections1.md)