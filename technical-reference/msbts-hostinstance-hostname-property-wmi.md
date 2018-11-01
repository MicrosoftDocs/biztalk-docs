---
title: MSBTS_HostInstance.HostName Property (WMI)
TOCTitle: MSBTS_HostInstance.HostName Property (WMI)
ms:assetid: 95fb1572-7ff1-4568-87ca-f368fdc6dad1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577437(v=BTS.80)
ms:contentKeyID: 51529839
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.HostName Property (WMI)

 

Contains the name of the BizTalk host to which this BizTalk host instance belongs.

## Property Declaration

*The syntax shown is language neutral.*

``` 
string HostName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

