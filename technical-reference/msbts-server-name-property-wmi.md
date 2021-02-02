---
description: "Learn more about: MSBTS_Server.Name Property (WMI)"
title: MSBTS_Server.Name Property (WMI)
TOCTitle: MSBTS_Server.Name Property (WMI)
ms:assetid: cd033a53-02f1-4be9-9e41-205bd749b973
ms:mtpsurl: https://msdn.microsoft.com/library/Aa548055(v=BTS.80)
ms:contentKeyID: 51531393
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server.Name Property (WMI)

 

Contains the name of the server.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string Name;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

This property is required for instance creation.

The maximum length for this property is 63 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

