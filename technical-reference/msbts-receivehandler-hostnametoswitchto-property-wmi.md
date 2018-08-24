---
title: MSBTS_ReceiveHandler.HostNameToSwitchTo Property (WMI)
TOCTitle: MSBTS_ReceiveHandler.HostNameToSwitchTo Property (WMI)
ms:assetid: 7b274a30-bfbe-4d6b-a7db-0c7567db70d6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560957(v=BTS.80)
ms:contentKeyID: 51529124
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveHandler.HostNameToSwitchTo Property (WMI)

 

Contains the name of the BizTalk Host that this adapter handler should switch to.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string HostNameToSwitchTo = "";  
```

## Remarks

This property is optional.

To switch this adapter to a different host, you must update this property with the name of the new host. This property is writeable during an update.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

