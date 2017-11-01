---
title: "fCanWeAdministerRemoteBox1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1da613f-3908-495d-9b2f-a90afd06f72d
caps.latest.revision: 3
---
# fCanWeAdministerRemoteBox
The **fCanWeAdministerRemoteBox** function is used to determine if the caller has administrative privileges on the remote computer. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL fCanWeAdministerRemoteBox(   
HKEY *hGlobalKey);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle to the remote computer's registry.  
  
## Return Value  
 TRUE  
 The caller has administrative privileges on the remote computer.  
  
 FALSE  
 The caller lacks administrative privileges.