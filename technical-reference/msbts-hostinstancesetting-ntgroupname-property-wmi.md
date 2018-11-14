---
title: MSBTS_HostInstanceSetting.NTGroupName Property (WMI)
TOCTitle: MSBTS_HostInstanceSetting.NTGroupName Property (WMI)
ms:assetid: 717f3c96-6f69-4be8-8252-481a4b965552
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560778(v=BTS.80)
ms:contentKeyID: 51528882
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting.NTGroupName Property (WMI)

 

Contains the name of the Microsoft® Windows NT® group.

## Property Declaration

*The syntax shown is language neutral.*

``` 
string NTGroupName;  
```

## Remarks

This property is read-only.

The Windows NT group can be either a local or a domain Windows NT group. The group is granted access to the application queue created for the host type. The account used to host the host instances must be a member of the group. For more information about accounts in BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](https://msdn.microsoft.com/library/aa577661\(v=bts.80\)).

The maximum length for this property is 63 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

