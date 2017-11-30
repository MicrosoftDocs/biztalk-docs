---
title: "sbpurcvx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 164d4f27-e7aa-4be7-afe8-254b4a40758b
caps.latest.revision: 3
---
# sbpurcvx
The **sbpurcvx** function processes Open responses from a routing procedure. An application can define a routing procedure that is called by the Dynamic Access Module (DMOD) when a message is received. This routing procedure should first call **sbpurcvx** to handle any Open response messages received. This ensures that Open responses intended for the Resource Locator are handled correctly.  
  
## Syntax  
  
```  
  
USHORT sbpurcvx(   
BUFHDR * *msgptr,   
INTEGER locl,   
INTEGER retstat  
);  
```  
  
#### Parameters  
 *msgptr*  
 Pointer to the message returned by the DMOD to the routing procedure.  
  
 *locl*  
 Locality from which message was received (if *retstat* indicates message returned), or locality to which path was lost (if *retstat* indicates path error).  
  
 *retstat*  
 Reason for call:  
  
 CEDINMSG (1—message returned.  
  
 CEDINLLN (2)—path error.  
  
## Return Value  
 TRUE  
 The Resource Locator has accepted the message; the application should not process it any further.  
  
 FALSE  
 The message should be processed by the application.  
  
## Remarks  
 This function is called by a routing procedure that is called by the DMOD. It is not called directly by the application.  
  
 The parameters for **sbpurcvx** should be taken from the parameters for [routproc](../HIS2010/routproc1.md). Note, however, that the first parameter to **sbpurcvx** is a pointer to a pointer to a buffer header (that is, a pointer to the corresponding parameter for the routing procedure, not the parameter itself).