---
title: MSBTS_HostSetting.NTGroupName Property (WMI)
TOCTitle: MSBTS_HostSetting.NTGroupName Property (WMI)
ms:assetid: 5e18ead8-6eef-4627-b75b-4d59748d247d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560398(v=BTS.80)
ms:contentKeyID: 51528366
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.NTGroupName Property (WMI)

 

Contains the name of the Windows NT group.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string NTGroupName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The Windows NT group can be either a local or a domain Windows NT group. The group is granted access to the application queue created for the application type. The account used to host the application instances must be a member of the group.

The maximum length for this property is 63 characters.

For sample code using the **MSBTS\_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](creating-updating-and-deleting-a-host-instance-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

