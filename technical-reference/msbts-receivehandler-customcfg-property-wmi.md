---
title: MSBTS_ReceiveHandler.CustomCfg Property (WMI)
TOCTitle: MSBTS_ReceiveHandler.CustomCfg Property (WMI)
ms:assetid: 97607975-232b-4888-bedd-5d90d8a5dac6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577460(v=BTS.80)
ms:contentKeyID: 51529852
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveHandler.CustomCfg Property (WMI)

 

Contains the adapter-specific configuration in XML format.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string CustomCfg;  
```

## Remarks

This property is read-write.

An empty value for this property means that the adapter is lacking important information and will not function correctly.

For more information about the configuring the receive location of any of the native adapters, see the following topics:

  - [How to Configure a File Receive Handler](https://msdn.microsoft.com/en-us/library/aa560577\(v=bts.80\))

  - [How to Configure an FTP Receive Handler](https://msdn.microsoft.com/en-us/library/aa561710\(v=bts.80\))

  - [How to Configure an HTTP Receive Handler](https://msdn.microsoft.com/en-us/library/aa547842\(v=bts.80\))

  - [How to Configure a SOAP Receive Handler](https://msdn.microsoft.com/en-us/library/aa561525\(v=bts.80\))

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

