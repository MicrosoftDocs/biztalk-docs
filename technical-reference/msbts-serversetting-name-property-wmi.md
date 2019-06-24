---
title: MSBTS_ServerSetting.Name Property (WMI)
TOCTitle: MSBTS_ServerSetting.Name Property (WMI)
ms:assetid: 76fe411f-77b2-4f97-a3c3-b3d4276e6bd0
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560871(v=BTS.80)
ms:contentKeyID: 51529016
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerSetting.Name Property (WMI)

 

Contains the name of the server.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string Name;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 63 characters.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

