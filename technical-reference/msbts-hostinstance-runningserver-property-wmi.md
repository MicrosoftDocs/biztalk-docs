---
title: MSBTS_HostInstance.RunningServer Property (WMI)
TOCTitle: MSBTS_HostInstance.RunningServer Property (WMI)
ms:assetid: 00b939e8-0800-4d8a-b09b-ddf399c19190
ms:mtpsurl: https://msdn.microsoft.com/library/Aa546741(v=BTS.80)
ms:contentKeyID: 51525859
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.RunningServer Property (WMI)

 

Contains the name of the server on which the host instance runs.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string RunningServer;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 63 characters.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

