---
description: "Learn more about: MSBTS_GroupSetting.SubscriptionDBServerName Property (WMI)"
title: MSBTS_GroupSetting.SubscriptionDBServerName Property (WMI)
TOCTitle: MSBTS_GroupSetting.SubscriptionDBServerName Property (WMI)
ms:assetid: 1ac5a718-ddb9-4307-a3e7-0d24b0dd7e98
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559048(v=BTS.80)
ms:contentKeyID: 51526573
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_GroupSetting.SubscriptionDBServerName Property (WMI)

 

Gets the name of the server running SQL Server where master subscription database is located.

The syntax shown is language neutral.

## Syntax

```C#
  
string SubscriptionDBServerName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

Maximum length for this property is 80 characters

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

