---
description: "Learn more about: MSBTS_Host.HostTracking Property (WMI)"
title: MSBTS_Host.HostTracking Property (WMI)
TOCTitle: MSBTS_Host.HostTracking Property (WMI)
ms:assetid: 32d3893f-a699-4ac4-99f6-e7ae08609a4e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559509(v=BTS.80)
ms:contentKeyID: 51527185
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.HostTracking Property (WMI)

 

Indicates whether instances of this BizTalk Host will host the tracking sub service.

## Property Declaration

*The syntax shown is language neutral.*

```C#
boolean HostTracking;  
```

## Remarks

This property is read-write.

At least one host in the group must host tracking. This option indicates whether the host loads the BizTalk Tracking component to process health monitoring and business data. Hosts that host tracking have read and write access to the tracking tables in the MessageBox database, as well as access to the tracking database. Therefore, any objects running in a host that hosts tracking also have access privileges to read and write to these database tables. Hosts that do not host tracking only have write access to the tracking tables in the MessageBox database, and no access to the tracking database.


> [!NOTE]
> <P>Specifying a host to host tracking has an impact on the performance of BizTalk Server.</P>



## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

