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
 [TPNameOverride](../HIS2010/tpnameoverride1.md)   
 [ProgNameOverride](../HIS2010/prognameoverride2.md)   
 [USERID](../HIS2010/userid2.md)   
 [PASSWORD](../HIS2010/password1.md)   
 [IMS_LTERM](../HIS2010/ims-lterm2.md)   
 [TRMIN](../HIS2010/trmin2.md)   
 [Custom TRMs and ELMs with COMTIContext](../HIS2010/custom-trms-and-elms-with-comticontext1.md)   
 [How to Pass a Custom TRM](../HIS2010/how-to-pass-a-custom-trm1.md)   
 [CONNTIMEOUT](../HIS2010/conntimeout1.md)