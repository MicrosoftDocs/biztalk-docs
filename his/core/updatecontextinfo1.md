---
description: "Learn more about: UpdateContextInfo"
title: "UpdateContextInfo1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# UpdateContextInfo
Use the **UpdateContextInfo** method to update the client **COMTIContext** array with the current state of the connection.  
  
## Syntax  
  
```  
  
HRESULT UpdateContextInfo (  
```  
  
#### Parameters  
 *COMTIContextArray*  
 This SAFEARRAY contains the state of the connection.  
  
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
 [DeleteContext](../core/deletecontext2.md)   
 [GetConnectionInfo](../core/getconnectioninfo2.md)   
 [QueryContextInfo](../core/querycontextinfo1.md)   
 [ReadContext](../core/readcontext1.md)   
 [WriteContext](../core/writecontext1.md)   
 [Persistent Connections](./persistent-connections2.md)
