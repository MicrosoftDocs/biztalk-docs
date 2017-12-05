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
 [ClearAllContext](../HIS2010/clearallcontext2.md)   
 [ClosePersistentConnection](../HIS2010/closepersistentconnection2.md)   
 [CountContext](../HIS2010/countcontext2.md)   
 [DeleteContext](../HIS2010/deletecontext1.md)   
 [QueryContextInfo](../HIS2010/querycontextinfo2.md)   
 [ReadContext](../HIS2010/readcontext2.md)   
 [UpdateContextInfo](../HIS2010/updatecontextinfo2.md)   
 [WriteContext](../HIS2010/writecontext2.md)   
 [Persistent Connections](../HIS2010/persistent-connections1.md)