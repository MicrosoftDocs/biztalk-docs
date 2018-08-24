---
title: MSBTS_Host.IsDefault Property (WMI)
TOCTitle: MSBTS_Host.IsDefault Property (WMI)
ms:assetid: f13c1666-0263-42b7-8b0e-770b246b44f4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561867(v=BTS.80)
ms:contentKeyID: 51533354
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.IsDefault Property (WMI)

 

Indicates whether the BizTalk Host represented by this WMI instance is the default BizTalk Host in the BizTalk group.

## Property Declaration

*The syntax shown is language neutral.*

``` 
boolean IsDefault;  
```

## Remarks

This property is read-write.

By default, BizTalk Server uses this host to host the orchestration during the orchestration enlistment process. The default host is by default the first host created. After you run the Configuration Wizard, the first In-process host is the default host for the BizTalk Group. You can explicitly choose a different host as the default for your BizTalk Server environment. You can identify the default host in the BizTalk Server Administration console because it has a checkmark symbol.


> [!NOTE]
> <P>You cannot delete a default host. You must first select a new default host.</P>




> [!NOTE]
> <P>When there is only one host in a BizTalk group, it cannot be deleted, as this is the default host.</P>




> [!NOTE]
> <P>Isolated hosts cannot be marked as the default host.</P>



## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

