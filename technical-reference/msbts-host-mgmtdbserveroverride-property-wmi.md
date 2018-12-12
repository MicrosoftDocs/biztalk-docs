---
title: MSBTS_Host.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_Host.MgmtDbServerOverride Property (WMI)
ms:assetid: 4a1a5f4b-006e-4d76-9897-0e2a6b342b32
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559971(v=BTS.80)
ms:contentKeyID: 51527824
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **Name**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

