---
title: "CONNTYPE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 86254232-aa1f-4f43-a66f-c0f02b222365
caps.latest.revision: 3
---
# CONNTYPE
Use the CONNTYPE keyword to establish a persistent connection by setting **CONNTYPE** to **OPEN**. If a call with **CONNTYPE** set to **OPEN** completes successfully, the returned **COMTIContext** array **CONNTYPE** keyword has a value of **USE**. To make a call and terminate the persistent connection, set the **CONNTYPE** keyword to **CLOSE**. If a call with **CONNTYPE** set to **CLOSE** completes successfully, the returned **COMTIContext** array **CONNTYPE** keyword has a value of **NONPERSISTENT**.  
  
## See Also  
 [TPNameOverride](../core/tpnameoverride1.md)   
 [ProgNameOverride](../core/prognameoverride2.md)   
 [USERID](../core/userid2.md)   
 [PASSWORD](../core/password1.md)   
 [IMS_LTERM](../core/ims-lterm2.md)   
 [TRMIN](../core/trmin2.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext1.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm1.md)   
 [CONNTIMEOUT](../core/conntimeout1.md)