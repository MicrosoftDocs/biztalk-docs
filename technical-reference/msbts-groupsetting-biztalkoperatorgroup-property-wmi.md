---
title: MSBTS_GroupSetting.BizTalkOperatorGroup Property (WMI)
TOCTitle: MSBTS_GroupSetting.BizTalkOperatorGroup Property (WMI)
ms:assetid: 41cffc6e-e587-47c9-a5f7-5d2f6c6fbe84
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559794(v=BTS.80)
ms:contentKeyID: 51527560
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.BizTalkOperatorGroup Property (WMI)

 

This property is the name of the BizTalk Operators Windows Group. Members of this Windows Group are granted permission to access BizTalk Monitoring functions. Certain functions require additional Windows or SQL privileges in addition to those granted by this group.

## Syntax

``` 
  
string BizTalkOperatorGroup;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 128 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

