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
  
-   [CONNTIMEOUT](../HIS2010/conntimeout1.md)  
  
-   [CONNTYPE](../HIS2010/conntype1.md)  
  
-   [IMS_LTERM](../HIS2010/ims-lterm2.md)  
  
-   [IMS_MODNAME](../HIS2010/ims-modname1.md)  
  
-   [LibNameOverride](../HIS2010/libnameoverride1.md)  
  
-   [OverrideSourceTP](../HIS2010/overridesourcetp2.md)  
  
-   [PASSWORD](../HIS2010/password1.md)  
  
-   [PortOverride](../HIS2010/portoverride2.md)  
  
-   [ProgNameOverride](../HIS2010/prognameoverride2.md)  
  
-   [RecvTimeOut](../HIS2010/recvtimeout2.md)  
  
-   [REOverride](../HIS2010/reoverride1.md)  
  
-   [SendTimeOut](../HIS2010/sendtimeout2.md)  
  
-   [TPNameOverride](../HIS2010/tpnameoverride1.md)  
  
-   [USERID](../HIS2010/userid2.md)  
  
 The override remains active until either a new override is set or the override is deleted. Use the **WriteContext** function to set the override and the **DeleteContext** function to delete the override. If you delete the override, the value defaults to the setting in the original type library.  
  
## See Also  
 [Custom TRMs and ELMs with COMTIContext](../HIS2010/custom-trms-and-elms-with-comticontext1.md)   
 [How to Pass a Custom TRM](../HIS2010/how-to-pass-a-custom-trm1.md)