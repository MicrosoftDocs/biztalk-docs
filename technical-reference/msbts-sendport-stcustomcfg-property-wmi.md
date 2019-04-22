---
title: MSBTS_SendPort.STCustomCfg Property (WMI)
TOCTitle: MSBTS_SendPort.STCustomCfg Property (WMI)
ms:assetid: 73561c8a-7308-4859-bac7-1b21404ebf3d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560814(v=BTS.80)
ms:contentKeyID: 51528962
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.STCustomCfg Property (WMI)

 

Contains transport type data for the secondary transport of the port.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string STCustomCfg;  
```

## Remarks

This method returns an HRESULT indicating whether the method completed successfully.

For more information about the configuring the receive location of any of the native adapters, see the following topics:

  - [How to Configure a File Send Port](https://msdn.microsoft.com/library/aa578662\(v=bts.80\))

  - [How to Configure an FTP Send Port](https://msdn.microsoft.com/library/aa546802\(v=bts.80\))

  - [How to Configure an HTTP Send Port](https://msdn.microsoft.com/library/aa559324\(v=bts.80\))

  - [How to Configure an SMTP Send Port](https://msdn.microsoft.com/library/aa578155\(v=bts.80\))

  - [How to Configure a SOAP Send Port](https://msdn.microsoft.com/library/aa559642\(v=bts.80\))

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

