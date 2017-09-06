---
title: "EncryptionCert (ReceiveLocation Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EncryptionCert node [binding file]"
ms.assetid: 04dc4021-8cd9-45e7-8339-8f22e29f4be6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EncryptionCert (ReceiveLocation Node)
The EncryptionCert node of the ReceiveLocation node of a binding file contains information about the encryption certificate used with a receive location that is exported with the binding file.  
  
## Nodes in the EncryptionCert node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|LongName|Attribute|xs:string|Specifies the long name of the certificate.|Not required|Default value: empty|  
|ShortName|Attribute|xs:string|Specifies the short name of the certificate.|Not required|Default value: empty|  
|UsageType|Attribute|CertUsageType (SimpleType)|Specifies the intended usage of this certificate|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx) enumeration.|  
|ThumbPrint|Attribute|xs:string|Specifies the thumbprint, or unique ID, of the certificate.|Not required|Default value: empty|