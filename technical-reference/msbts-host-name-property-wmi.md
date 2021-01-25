---
description: "Learn more about: MSBTS_Host.Name Property (WMI)"
title: MSBTS_Host.Name Property (WMI)
TOCTitle: MSBTS_Host.Name Property (WMI)
ms:assetid: 296f8fea-fc9e-49e0-a46c-3403f7d7d038
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559319(v=BTS.80)
ms:contentKeyID: 51526976
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.Name Property (WMI)

 

Contains the name of the host.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string Name;  
```

## Remarks

This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

