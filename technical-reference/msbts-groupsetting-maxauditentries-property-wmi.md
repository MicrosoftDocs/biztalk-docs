---
description: "Learn more about: MSBTS_GroupSetting.MaxAuditEntries Property (WMI)"
title: MSBTS_GroupSetting.MaxAuditEntries Property (WMI)
TOCTitle: MSBTS_GroupSetting.MaxAuditEntries Property (WMI)
ms.date: 09/13/2021
---

# MSBTS\_GroupSetting.MaxAuditEntries Property (WMI)

 

Gets or sets the maximum number of entries in audit log table when auditing is enabled. 

Available BizTalk Server 2020 onwards. Please see how to [enable and view audit logs of common management operations in BizTalk Server](../audit-management-operations.md) for further details.

The syntax shown is language neutral.

## Syntax

```C#
  
uint32 MaxAuditEntries;  
```

## Remarks

This property is read-write. 

The default value for this property is 10000.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
