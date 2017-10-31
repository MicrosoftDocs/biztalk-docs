---
title: "IMS_LTERM1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44fd75f4-2dbc-41cc-884e-f03310198030
caps.latest.revision: 3
---
# IMS_LTERM
Use the **IMS_LTERM** to override the default LTERM that an Information Management Systems (IMS) connect call uses while processing the host transaction within IMS. The COMTIContext context name is **IMS_LTERM**, and its value must be from one through eight alphanumeric characters.  
  
> [!NOTE]
>  If the **IMS_LTERM** is assigned more than eight characters, the **IMS_LTERM** value is not passed to the host transaction and the host transaction continues to use the system provided default LTERM.  
  
## See Also  
 [REOverride](../core/reoverride.md)   
 [TPNameOverride](../core/tpnameoverride.md)   
 [ProgNameOverride](../core/prognameoverride.md)   
 [USERID](../core/userid.md)   
 [PASSWORD](../core/password.md)   
 [TRMIN](../core/trmin.md)   
 [TRMOUT](../core/trmout.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm.md)