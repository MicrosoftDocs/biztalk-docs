---
title: "IMS_LTERM2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3777e305-1fb8-4ea6-8a1b-f58ebb7756a5
caps.latest.revision: 3
---
# IMS_LTERM
Use the **IMS_LTERM** to override the default LTERM that an Information Management Systems (IMS) connect call uses while processing the host transaction within IMS. The COMTIContext context name is **IMS_LTERM**, and its value must be from one through eight alphanumeric characters.  
  
> [!NOTE]
>  If the **IMS_LTERM** is assigned more than eight characters, the **IMS_LTERM** value is not passed to the host transaction and the host transaction continues to use the system provided default LTERM.  
  
## See Also  
 [REOverride](../HIS2010/reoverride1.md)   
 [TPNameOverride](../HIS2010/tpnameoverride1.md)   
 [ProgNameOverride](../HIS2010/prognameoverride2.md)   
 [USERID](../HIS2010/userid2.md)   
 [PASSWORD](../HIS2010/password1.md)   
 [TRMIN](../HIS2010/trmin2.md)   
 [TRMOUT](../HIS2010/trmout1.md)   
 [Custom TRMs and ELMs with COMTIContext](../HIS2010/custom-trms-and-elms-with-comticontext1.md)   
 [How to Pass a Custom TRM](../HIS2010/how-to-pass-a-custom-trm1.md)