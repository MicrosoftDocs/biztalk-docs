---
title: "CONNTYPE2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57f4b1d5-3c1c-4d74-94e9-fc9969671f8d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# CONNTYPE
Use the CONNTYPE keyword to establish a persistent connection by setting **CONNTYPE** to **OPEN**. If a call with **CONNTYPE** set to **OPEN** completes successfully, the returned **COMTIContext** array **CONNTYPE** keyword has a value of **USE**. To make a call and terminate the persistent connection, set the **CONNTYPE** keyword to **CLOSE**. If a call with **CONNTYPE** set to **CLOSE** completes successfully, the returned **COMTIContext** array **CONNTYPE** keyword has a value of **NONPERSISTENT**.  
  
## See Also  
 [TPNameOverride](../core/tpnameoverride.md)   
 [ProgNameOverride](../core/prognameoverride.md)   
 [USERID](../core/userid.md)   
 [PASSWORD](../core/password.md)   
 [IMS_LTERM](../core/ims-lterm.md)   
 [TRMIN](../core/trmin.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm.md)   
 [CONNTIMEOUT](../core/conntimeout.md)