---
description: "Learn more about: ClearAllContext"
title: "ClearAllContext1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [ClosePersistentConnection](../core/closepersistentconnection1.md)   
 [CountContext](../core/countcontext1.md)   
 [DeleteContext](../core/deletecontext2.md)   
 [GetConnectionInfo](../core/getconnectioninfo2.md)   
 [QueryContextInfo](../core/querycontextinfo1.md)   
 [ReadContext](../core/readcontext1.md)   
 [UpdateContextInfo](../core/updatecontextinfo1.md)   
 [WriteContext](../core/writecontext1.md)   
 [Persistent Connections](./persistent-connections2.md)
