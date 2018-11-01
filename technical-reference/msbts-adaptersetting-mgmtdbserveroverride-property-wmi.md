---
title: MSBTS_AdapterSetting.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_AdapterSetting.MgmtDbServerOverride Property (WMI)
ms:assetid: 31406f08-3d32-4715-a3ef-a58c79d3540c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559479(v=BTS.80)
ms:contentKeyID: 51527131
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_AdapterSetting.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with [MgmtDbNameOverride](msbts-adaptersetting-mgmtdbnameoverride-property-wmi.md) and [Name](msbts-adaptersetting-name-property-wmi.md), this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

