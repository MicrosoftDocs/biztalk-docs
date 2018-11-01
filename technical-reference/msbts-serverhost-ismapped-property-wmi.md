---
title: MSBTS_ServerHost.IsMapped Property (WMI)
TOCTitle: MSBTS_ServerHost.IsMapped Property (WMI)
ms:assetid: 0c967535-3cea-42b2-a852-4a0013557c64
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547305(v=BTS.80)
ms:contentKeyID: 51526161
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.IsMapped Property (WMI)

 

Indicates whether the specified server works with the specified MessageBox.

## Property Declaration

*The syntax shown is language neutral.*

``` 
boolean IsMapped;  
```

## Remarks

BizTalk Server consumes messages from the MessageBox when **IsMapped** is set to **true**; when set to **false**, BizTalk Server does not consume messages from the MessageBox.

This property is read-only.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

