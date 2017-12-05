---
title: "Host Column Description | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eabde5d8-2a34-4967-afc3-43049e8591bc
caps.latest.revision: 3
---
# Host Column Description
The Microsoft® OLE DB Provider for AS/400 and VSAM uses a host column description (HCD) file to specify how data on the host is converted by the OLE DB provider. These HCD files are not necessary when used with IBM AS/400 computers because the host data format is automatically determined by the OLE DB provider. When used with AS/400 computers, the OLE DB provider uses default conversions from host data type to OLE DB data types. However, HCD files can be used with AS/400 computers to override the host data format and specify a particular local OLE DB data type to which the data is to be converted.  
  
 The following topics describe the host column description file format in detail and provide an example of an HCD file for illustration.  
  
 This section contains:  
  
-   [Host Column Description File Format](../core/host-column-description-file-format.md)  
  
-   [Host Column Description Attributes](../core/host-column-description-attributes.md)  
  
-   [Host Column Description Example File](../core/host-column-description-example-file.md)