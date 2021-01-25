---
description: "Learn more about: MSBTS_Host.MgmtDbNameOverride Property (WMI)"
title: MSBTS_Host.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_Host.MgmtDbNameOverride Property (WMI)
ms:assetid: 01016b90-8d6e-4515-a3cc-27abd98908b0
ms:mtpsurl: https://msdn.microsoft.com/library/Aa546746(v=BTS.80)
ms:contentKeyID: 51525862
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride** and **Name**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

