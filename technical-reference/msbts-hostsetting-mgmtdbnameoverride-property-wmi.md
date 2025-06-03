---
description: "Learn more about: MSBTS_HostSetting.MgmtDbNameOverride Property (WMI)"
title: MSBTS_HostSetting.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_HostSetting.MgmtDbNameOverride Property (WMI)
ms:assetid: 176e4f6c-f854-41ca-a615-56d43ada6afb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558772(v=BTS.80)
ms:contentKeyID: 51526438
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostSetting.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride** and **Name**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

For sample code using the **MSBTS\_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](creating-updating-and-deleting-a-host-instance-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

