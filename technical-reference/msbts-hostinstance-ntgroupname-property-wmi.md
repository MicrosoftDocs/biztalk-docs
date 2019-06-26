---
title: MSBTS_HostInstance.NTGroupName Property (WMI)
TOCTitle: MSBTS_HostInstance.NTGroupName Property (WMI)
ms:assetid: 7e54d0e9-ced7-4884-89ec-bbc96b8a77d9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561025(v=BTS.80)
ms:contentKeyID: 51529215
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.NTGroupName Property (WMI)

 

Contains the name of the Microsoft Windows NT group.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string NTGroupName;  
```

## Remarks

This property is read only.

The Windows NT group can be either a local or a domain Windows NT group. The group is granted access to the application queue created for the host type. The account used to host the host instances must be a member of the group. For more information about accounts in BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](https://msdn.microsoft.com/library/aa577661\(v=bts.80\)).

The maximum length for this property is 63 characters.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

