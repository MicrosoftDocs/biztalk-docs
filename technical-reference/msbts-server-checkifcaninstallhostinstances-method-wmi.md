---
title: MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI)
TOCTitle: MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI)
ms:assetid: ceae4612-a215-45b7-a210-be9d39d17be6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578491(v=BTS.80)
ms:contentKeyID: 51531340
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server.CheckIfCanInstallHostInstances Method (WMI)

 

Checks if the server can host BizTalk host instances.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 CheckIfCanInstallHostInstances();  
```

## Error Handling

S\_OK (0) if yes, S\_FALSE (1) if no, and FAILED (negative) if otherwise.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

