---
title: "UpdateContextInfo1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed86e0a4-57e3-4270-adc9-6d7db7d32e6f
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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
 [ClearAllContext](../core/clearallcontext.md)   
 [ClosePersistentConnection](../core/closepersistentconnection.md)   
 [CountContext](../core/countcontext.md)   
 [DeleteContext](../core/deletecontext.md)   
 [GetConnectionInfo](../core/getconnectioninfo.md)   
 [QueryContextInfo](../core/querycontextinfo.md)   
 [ReadContext](../core/readcontext.md)   
 [WriteContext](../core/writecontext.md)   
 [Persistent Connections](../Topic/Persistent%20Connections1.md)