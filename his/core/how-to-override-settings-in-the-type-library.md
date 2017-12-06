---
title: "How To Override Settings in the Type Library2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63b686be-8ec7-4ebb-b48d-20dc8ce04069
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How To Override Settings in the Type Library
If you need to temporarily change certain data sent from the type library to the host, you can override the type library settings without changing the original file. Use the following keywords in combination with the COMTIContext parameter to override the type library setting:  
  
-   [CONNTIMEOUT](../Topic/CONNTIMEOUT1.md)  
  
-   [CONNTYPE](../Topic/CONNTYPE1.md)  
  
-   [IMS_LTERM](../Topic/IMS_LTERM2.md)  
  
-   [IMS_MODNAME](../Topic/IMS_MODNAME1.md)  
  
-   [LibNameOverride](../Topic/LibNameOverride1.md)  
  
-   [OverrideSourceTP](../Topic/OverrideSourceTP2.md)  
  
-   [PASSWORD](../Topic/PASSWORD1.md)  
  
-   [PortOverride](../Topic/PortOverride2.md)  
  
-   [ProgNameOverride](../Topic/ProgNameOverride2.md)  
  
-   [RecvTimeOut](../Topic/RecvTimeOut2.md)  
  
-   [REOverride](../Topic/REOverride1.md)  
  
-   [SendTimeOut](../Topic/SendTimeOut2.md)  
  
-   [TPNameOverride](../Topic/TPNameOverride1.md)  
  
-   [USERID](../Topic/USERID2.md)  
  
 The override remains active until either a new override is set or the override is deleted. Use the **WriteContext** function to set the override and the **DeleteContext** function to delete the override. If you delete the override, the value defaults to the setting in the original type library.  
  
## See Also  
 [Custom TRMs and ELMs with COMTIContext](../Topic/Custom%20TRMs%20and%20ELMs%20with%20COMTIContext1.md)   
 [How to Pass a Custom TRM](../Topic/How%20to%20Pass%20a%20Custom%20TRM1.md)