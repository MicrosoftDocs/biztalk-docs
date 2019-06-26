---
title: MSBTS_HostSetting.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_HostSetting.MgmtDbServerOverride Property (WMI)
ms:assetid: f6b157a0-1bea-4969-a37f-8d192ce58c9e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561977(v=BTS.80)
ms:contentKeyID: 51533488
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **Name**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

For sample code using the **MSBTS\_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](creating-updating-and-deleting-a-host-instance-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

