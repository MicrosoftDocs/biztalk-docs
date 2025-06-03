---
description: "Learn more about: MSBTS_HostQueue.MgmtDbNameOverride Property (WMI)"
title: MSBTS_HostQueue.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_HostQueue.MgmtDbNameOverride Property (WMI)
ms:assetid: cca068e8-4148-493b-93c7-bac34dfa7aa7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa548048(v=BTS.80)
ms:contentKeyID: 51531381
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostQueue.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-only.

This property has a **Key** qualifier. Along with **HostName** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

