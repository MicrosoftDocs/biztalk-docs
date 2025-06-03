---
description: "Learn more about: MSBTS_HostQueue.MgmtDbServerOverride Property (WMI)"
title: MSBTS_HostQueue.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_HostQueue.MgmtDbServerOverride Property (WMI)
ms:assetid: 13b369e3-8ba2-4414-8368-5268c873c827
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547626(v=BTS.80)
ms:contentKeyID: 51526386
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostQueue.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Managemetn database connect string. This property was not implemented for BizTalk Server and is reserved for future use.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-only.

This property has a **Key** qualifier. Along with **HostName** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

