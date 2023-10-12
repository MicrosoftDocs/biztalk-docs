---
description: "Learn more about: fCanWeAdministerRemoteBox"
title: "fCanWeAdministerRemoteBox1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
