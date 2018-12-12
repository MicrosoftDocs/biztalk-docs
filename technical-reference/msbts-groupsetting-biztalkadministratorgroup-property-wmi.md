---
title: MSBTS_GroupSetting.BizTalkAdministratorGroup Property (WMI)
TOCTitle: MSBTS_GroupSetting.BizTalkAdministratorGroup Property (WMI)
ms:assetid: d848685e-5156-4647-aa60-c42a6a03d70f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578669(v=BTS.80)
ms:contentKeyID: 51531716
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.BizTalkAdministratorGroup Property (WMI)

 

Gets the name of the BizTalk Administrator Windows NT Group. Only members of this Windows NT Group have permissions to access BizTalk Administration functions.

The syntax shown is language neutral.

## Syntax

```C#
  
string BizTalkAdministratorGroup;  
```

## Remarks

Only members of this Windows NT Group have permissions to access BizTalk Administration functions.

Certain functions require additional Windows or SQL privileges; refer to BizTalk Server Help for more details.

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

Maximum length for this property is 63 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

