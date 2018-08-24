---
title: MSBTS_SendPort.PTCustomCfg Property (WMI)
TOCTitle: MSBTS_SendPort.PTCustomCfg Property (WMI)
ms:assetid: 66d7b8d7-9cc7-4197-bc58-21752364177f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560550(v=BTS.80)
ms:contentKeyID: 51528601
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.PTCustomCfg Property (WMI)

 

Contains transport type data for the primary transport of the port.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string PTCustomCfg;  
```

## Remarks

This property is read-write.

For more information about the configuring the receive location of any of the native adapters, see the following topics:

  - [How to Configure a File Send Port](https://msdn.microsoft.com/en-us/library/aa578662\(v=bts.80\))

  - [How to Configure an FTP Send Port](https://msdn.microsoft.com/en-us/library/aa546802\(v=bts.80\))

  - [How to Configure an HTTP Send Port](https://msdn.microsoft.com/en-us/library/aa559324\(v=bts.80\))

  - [How to Configure an SMTP Send Port](https://msdn.microsoft.com/en-us/library/aa578155\(v=bts.80\))

  - [How to Configure a SOAP Send Port](https://msdn.microsoft.com/en-us/library/aa559642\(v=bts.80\))

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

