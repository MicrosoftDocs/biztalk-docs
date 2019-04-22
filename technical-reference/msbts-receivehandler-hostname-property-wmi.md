---
title: MSBTS_ReceiveHandler.HostName Property (WMI)
TOCTitle: MSBTS_ReceiveHandler.HostName Property (WMI)
ms:assetid: 6bc93b56-3ae7-4b99-a5be-19dd73e43872
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560662(v=BTS.80)
ms:contentKeyID: 51528746
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveHandler.HostName Property (WMI)

 

Contains the name of the BizTalk Host for this adapter.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string HostName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a Key qualifier. Along with **AdapterName**, **MgmtDbServerOverride**, and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

