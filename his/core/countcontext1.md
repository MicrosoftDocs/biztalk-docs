---
description: "Learn more about: CountContext"
title: "CountContext1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [ClearAllContext](../core/clearallcontext1.md)   
 [ClosePersistentConnection](../core/closepersistentconnection1.md)   
 [DeleteContext](../core/deletecontext2.md)   
 [GetConnectionInfo](../core/getconnectioninfo2.md)   
 [QueryContextInfo](../core/querycontextinfo1.md)   
 [ReadContext](../core/readcontext1.md)   
 [UpdateContextInfo](../core/updatecontextinfo1.md)   
 [WriteContext](../core/writecontext1.md)   
 [Persistent Connections](./persistent-connections2.md)
