---
title: MSBTS_ReceiveLocation.CustomCfg Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.CustomCfg Property (WMI)
ms:assetid: 50db0788-b49c-484b-8fa6-e5f002a32e72
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560129(v=BTS.80)
ms:contentKeyID: 51527992
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.CustomCfg Property (WMI)

 

Contains the adapter-specific configuration in XML format.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string CustomCfg;  
```

## Remarks

This property is read-write.

An empty value for this property means that the adapter is lacking some important information and will not function correctly.

For more information about the configuring the receive location of any of the native adapters, see the following topics:

  - [How to Configure an HTTP Receive Location](https://msdn.microsoft.com/en-us/library/aa561370\(v=bts.80\))

  - [How to Configure an FTP Receive Location](https://msdn.microsoft.com/en-us/library/aa559095\(v=bts.80\))

  - [How to Configure a File Receive Location](https://msdn.microsoft.com/en-us/library/aa547108\(v=bts.80\))

  - [How to Configure MQSeries Adapter Receive Locations and Send Ports](https://msdn.microsoft.com/en-us/library/aa560215\(v=bts.80\))

  - [How to Configure an MSMQ Receive Location](https://msdn.microsoft.com/en-us/library/aa578322\(v=bts.80\))

  - [How to Configure a POP3 Receive Location](https://msdn.microsoft.com/en-us/library/aa559245\(v=bts.80\))

  - [How to Configure a SOAP Receive Location](https://msdn.microsoft.com/en-us/library/aa561021\(v=bts.80\))

  - [How to Configure a Windows SharePoint Services Receive Location](https://msdn.microsoft.com/en-us/library/aa560390\(v=bts.80\))

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

