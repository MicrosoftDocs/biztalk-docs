---
title: MSBTS_MsgBoxSetting.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_MsgBoxSetting.MgmtDbNameOverride Property (WMI)
ms:assetid: 0fa086a5-f85d-4acc-98d9-2bbd7723fac7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547541(v=BTS.80)
ms:contentKeyID: 51526270
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MsgBoxSetting.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride**, **MsgBoxDBName**, and **MsgBoxDBServerName**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

