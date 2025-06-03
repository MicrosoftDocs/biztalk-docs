---
description: "Learn more about: MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI)"
title: MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI)
ms:assetid: 303efd7c-d33b-4253-8b36-398587494ec2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559457(v=BTS.80)
ms:contentKeyID: 51527106
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_SendHandler2.MgmtDbNameOverride Property (WMI)

 

This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name. Max length for this property is 123 characters.

string MgmtDbNameOverride="";

## Syntax

```C#
  
string MgmtDbNameOverride;  
```

## Remarks

This property is read/write.

The syntax shown is language neutral.

The default value for this property is "".

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

