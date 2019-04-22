---
title: MSBTS_ServerSetting.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_ServerSetting.MgmtDbNameOverride Property (WMI)
ms:assetid: 3cae05e9-9b91-4b38-9b5f-b4a5bd0fd48c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559698(v=BTS.80)
ms:contentKeyID: 51527489
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerSetting.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

