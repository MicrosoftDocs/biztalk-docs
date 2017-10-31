---
title: "GetConnectionInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d261c1e-c53f-4b2a-825e-ce9c9828a2c1
caps.latest.revision: 3
---
# GetConnectionInfo
Use the **GetConnectionInfo** method to query the state of the persistent connection.  
  
## Syntax  
  
```  
  
HRESULT GetConnectionInfo (  
```  
  
#### Parameters  
 *COMTIContextArray*  
 This SAFEARRAY contains the state of the connection.  
  
 *pfConnectionIsPersistent*  
 This BOOL parameter is set to TRUE if the connection is persistent and active.  
  
 *pfConnectionIsViable*  
 This BOOL parameter is set to TRUE if the connection is active.  
  
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
 [QueryContextInfo](../core/querycontextinfo.md)   
 [ReadContext](../core/readcontext.md)   
 [UpdateContextInfo](../core/updatecontextinfo.md)   
 [WriteContext](../core/writecontext.md)   
 [Persistent Connections](../Topic/Persistent%20Connections1.md)