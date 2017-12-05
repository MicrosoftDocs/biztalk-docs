---
title: "ReadContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3add04b2-3db1-4264-9bdc-7962d65d8f48
caps.latest.revision: 3
---
# ReadContext
Use the **ReadContext** method to acquire the value of an entry in a TI Context array.  
  
## Syntax  
  
```  
  
HRESULT ReadContext (  
```  
  
#### Parameters  
 *bstrContextEntryName*  
 This string parameter contains the name of the TI Context entry to be retrieved.  
  
 *pvarContextEntryValue*  
 This VARIANT parameter contains the value of the context entry identified by bstrContextEntryName.  
  
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
 [ClearAllContext](../core/clearallcontext2.md)   
 [ClosePersistentConnection](../core/closepersistentconnection2.md)   
 [CountContext](../core/countcontext2.md)   
 [DeleteContext](../core/deletecontext1.md)   
 [GetConnectionInfo](../core/getconnectioninfo1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [UpdateContextInfo](../core/updatecontextinfo2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Persistent Connections](../core/persistent-connections1.md)