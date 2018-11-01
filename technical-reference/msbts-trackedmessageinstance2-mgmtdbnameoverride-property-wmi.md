---
title: MSBTS_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI)
ms:assetid: 400c9b09-ce2a-4a52-b129-450d7984ef12
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559762(v=BTS.80)
ms:contentKeyID: 51527520
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI)

 

This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name.

## Syntax

``` 
  
string MgmtDbNameOverride;  
```

## Remarks

This parameter is read/write.

The syntax shown is language neutral.

The default value for this parameter is "".

The maximum length for this parameter is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

