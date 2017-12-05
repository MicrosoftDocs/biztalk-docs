---
title: "GetConnectionInfo1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffaefbb4-ce47-40c8-ab03-971c848b99c5
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
 [ClearAllContext](../core/clearallcontext2.md)   
 [ClosePersistentConnection](../core/closepersistentconnection2.md)   
 [CountContext](../core/countcontext2.md)   
 [DeleteContext](../core/deletecontext1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [ReadContext](../core/readcontext2.md)   
 [UpdateContextInfo](../core/updatecontextinfo2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Persistent Connections](../core/persistent-connections1.md)