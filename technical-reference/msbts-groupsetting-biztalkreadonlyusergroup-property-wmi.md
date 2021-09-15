---
description: "Learn more about: MSBTS_GroupSetting.BizTalkReadOnlyUserGroup Property (WMI)"
title: MSBTS_GroupSetting.BizTalkReadOnlyUserGroup Property (WMI)
TOCTitle: MSBTS_GroupSetting.BizTalkReadOnlyUserGroup Property (WMI)
ms.date: 09/13/2021
---

# MSBTS\_GroupSetting.BizTalkReadOnlyUserGroup Property (WMI)

 

Gets the name of the BizTalk ReadOnly User Windows Group. Members of this Windows Group are granted permission to view Artifact, Service, Message and Tracking Information. Certain functions require additional Windows or SQL privileges in addition to those granted by this group.

## Syntax

```C#
  
string BizTalkReadOnlyUserGroup;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 128 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
