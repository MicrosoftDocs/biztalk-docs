---
description: "Learn more about: MSBTS_GroupSetting.SubscriptionDBName Property (WMI)"
title: MSBTS_GroupSetting.SubscriptionDBName Property (WMI)
TOCTitle: MSBTS_GroupSetting.SubscriptionDBName Property (WMI)
ms:assetid: 5af4eefa-9cac-4756-b311-d133ab0e1bd7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560331(v=BTS.80)
ms:contentKeyID: 51528269
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.SubscriptionDBName Property (WMI)

 

Gets the name of the master subscription SQL database.

The syntax shown is language neutral.

## Syntax

```C#
  
string SubscriptionDBName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

Maximum length for this property is 100 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

