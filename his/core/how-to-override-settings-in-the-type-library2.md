---
title: "How To Override Settings in the Type Library2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63b686be-8ec7-4ebb-b48d-20dc8ce04069
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How To Override Settings in the Type Library
If you need to temporarily change certain data sent from the type library to the host, you can override the type library settings without changing the original file. Use the following keywords in combination with the COMTIContext parameter to override the type library setting:  
  
-   [CONNTIMEOUT](../core/conntimeout1.md)  
  
-   [CONNTYPE](../core/conntype1.md)  
  
-   [IMS_LTERM](../core/ims-lterm2.md)  
  
-   [IMS_MODNAME](../core/ims-modname1.md)  
  
-   [LibNameOverride](../core/libnameoverride1.md)  
  
-   [OverrideSourceTP](../core/overridesourcetp2.md)  
  
-   [PASSWORD](../core/password1.md)  
  
-   [PortOverride](../core/portoverride2.md)  
  
-   [ProgNameOverride](../core/prognameoverride2.md)  
  
-   [RecvTimeOut](../core/recvtimeout2.md)  
  
-   [REOverride](../core/reoverride1.md)  
  
-   [SendTimeOut](../core/sendtimeout2.md)  
  
-   [TPNameOverride](../core/tpnameoverride1.md)  
  
-   [USERID](../core/userid2.md)  
  
 The override remains active until either a new override is set or the override is deleted. Use the **WriteContext** function to set the override and the **DeleteContext** function to delete the override. If you delete the override, the value defaults to the setting in the original type library.  
  
## See Also  
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext1.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm1.md)