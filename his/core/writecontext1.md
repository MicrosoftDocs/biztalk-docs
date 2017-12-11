---
title: "WriteContext1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f1bfc3b-a195-440d-844e-23f71e2e2926
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WriteContext
Use the **WriteContext** function to add or replace an entry in a TI Context array.  
  
## Syntax  
  
```  
  
HRESULT WriteContext (  
```  
  
#### Parameters  
 *bstrContextEntryName*  
 This string parameter contains the name under which the TI Context entry will be stored and accessed. Some context entry names are predefined by Microsoft. You are free to define your own (although there is no way to deal with such in the COM+ application).  
  
 *varContextEntryValue*  
 This VARIANT parameter contains the value to be stored for the context entry identified by bstrContextEntryName.  
  
 *prgContextArray*  
 This SAFEARRAY parameter contains the TI Context entries that are passed to and returned from COM+ objects.  
  
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
 [UpdateContextInfo](../core/updatecontextinfo1.md)   
 [Persistent Connections](../HIS2010/persistent-connections1.md)