---
title: MSBTS_ReceiveHandler.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ReceiveHandler.MgmtDbServerOverride Property (WMI)
ms:assetid: 6ea637b5-ecac-460b-9338-ea9fadb59842
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560724(v=BTS.80)
ms:contentKeyID: 51528808
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveHandler.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **AdapterName**, **HostName**, and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

