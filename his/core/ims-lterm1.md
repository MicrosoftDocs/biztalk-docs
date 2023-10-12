---
description: "Learn more about: IMS_LTERM"
title: "IMS_LTERM1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# IMS_LTERM
Use the **IMS_LTERM** to override the default LTERM that an Information Management Systems (IMS) connect call uses while processing the host transaction within IMS. The COMTIContext context name is **IMS_LTERM**, and its value must be from one through eight alphanumeric characters.  
  
> [!NOTE]
>  If the **IMS_LTERM** is assigned more than eight characters, the **IMS_LTERM** value is not passed to the host transaction and the host transaction continues to use the system provided default LTERM.  
  
## See Also  
 [REOverride](../core/reoverride2.md)   
 [TPNameOverride](../core/tpnameoverride2.md)   
 [ProgNameOverride](../core/prognameoverride1.md)   
 [USERID](../core/userid1.md)   
 [PASSWORD](../core/password2.md)   
 [TRMIN](../core/trmin1.md)   
 [TRMOUT](../core/trmout2.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext2.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm2.md)
