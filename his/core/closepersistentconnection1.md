---
description: "Learn more about: ClosePersistentConnection"
title: "ClosePersistentConnection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4b46091-0d66-44cb-a714-c56f5572eb0c
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
 [ClearAllContext](../core/clearallcontext1.md)   
 [CountContext](../core/countcontext1.md)   
 [DeleteContext](../core/deletecontext2.md)   
 [GetConnectionInfo](../core/getconnectioninfo2.md)   
 [QueryContextInfo](../core/querycontextinfo1.md)   
 [ReadContext](../core/readcontext1.md)   
 [UpdateContextInfo](../core/updatecontextinfo1.md)   
 [WriteContext](../core/writecontext1.md)   
 [Persistent Connections](./persistent-connections2.md)
