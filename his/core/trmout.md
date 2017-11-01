---
title: "TRMOUT2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f7f9bde-ac0a-464e-a820-8c0ae012c15a
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# TRMOUT
Use the **TRMOUT** keyword to override the default transaction request message (TRM) containing the transaction program ID, user ID, password, and other administrative data sent from the host. The COMTIContext context name is **TRMOUT**. The TRM must be defined as a user-defined type (UDT), and the name of that UDT must begin with the characters TRMOUT.  
  
## See Also  
 [TPNameOverride](../core/tpnameoverride.md)   
 [ProgNameOverride](../core/prognameoverride.md)   
 [USERID](../core/userid.md)   
 [PASSWORD](../core/password.md)   
 [IMS_LTERM](../core/ims-lterm.md)   
 [TRMIN](../core/trmin.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm.md)