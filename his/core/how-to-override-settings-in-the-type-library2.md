---
description: "Learn more about: How To Override Settings in the Type Library"
title: "How To Override Settings in the Type Library2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How To Override Settings in the Type Library
If you need to temporarily change certain data sent from the type library to the host, you can override the type library settings without changing the original file. Use the following keywords in combination with the COMTIContext parameter to override the type library setting:  
  
- [CONNTIMEOUT](./conntimeout2.md)  
  
- [CONNTYPE](./conntype2.md)  
  
- [IMS_LTERM](./ims-lterm1.md)  
  
- [IMS_MODNAME](./ims-modname2.md)  
  
- [LibNameOverride](./libnameoverride2.md)  
  
- [OverrideSourceTP](./overridesourcetp1.md)  
  
- [PASSWORD](./password2.md)  
  
- [PortOverride](./portoverride1.md)  
  
- [ProgNameOverride](./prognameoverride1.md)  
  
- [RecvTimeOut](./recvtimeout1.md)  
  
- [REOverride](./reoverride2.md)  
  
- [SendTimeOut](./sendtimeout1.md)  
  
- [TPNameOverride](./tpnameoverride2.md)  
  
- [USERID](./userid1.md)  
  
  The override remains active until either a new override is set or the override is deleted. Use the **WriteContext** function to set the override and the **DeleteContext** function to delete the override. If you delete the override, the value defaults to the setting in the original type library.  
  
## See Also  
 [Custom TRMs and ELMs with COMTIContext](./custom-trms-and-elms-with-comticontext2.md)   
 [How to Pass a Custom TRM](./how-to-pass-a-custom-trm2.md)
