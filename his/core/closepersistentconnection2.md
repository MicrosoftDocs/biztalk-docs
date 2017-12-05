---
title: "ClosePersistentConnection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 734f541b-7528-480f-97c3-258101e4081d
caps.latest.revision: 3
---
# ClosePersistentConnection
Use the **ClosePersistentConnection** method to close the persistent connection by contacting the COM+ or .NET Framework application object without the need for a call to the server object.  
  
## Syntax  
  
```  
  
HRESULT ClosePersistentConnection (  
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
 [ClearAllContext](../core/clearallcontext2.md)   
 [CountContext](../core/countcontext2.md)   
 [DeleteContext](../core/deletecontext1.md)   
 [GetConnectionInfo](../core/getconnectioninfo1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [ReadContext](../core/readcontext2.md)   
 [UpdateContextInfo](../core/updatecontextinfo2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Persistent Connections](../core/persistent-connections1.md)