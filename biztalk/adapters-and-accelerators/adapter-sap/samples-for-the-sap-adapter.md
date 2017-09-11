---
title: "Samples for the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "samples, Data Provider for SAP"
  - "samples, migration"
  - "samples, BizTalk"
  - "samples, WCF service model"
  - "samples, WCF channel model"
  - "samples"
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the SAP adapter
Samples for [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] are categorized into:  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  
  
-   WCF service model samples  
  
-   WCF channel model samples  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] samples  
  
-   Migration samples  
  
 The samples are available at [http://go.microsoft.com/fwlink/?LinkID=196854](http://go.microsoft.com/fwlink/?LinkID=196854).  
  
 The following list contains the names and descriptions of the samples for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## BizTalk Server Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|IDOCSend|Demonstrates how to send an IDOC to an SAP system.|  
|ReceiveIDOC|Demonstrates how to receive an IDOC from an SAP system.|  
|ReceiveIDOC_SYSREL|Demonstrates how to receive an IDOC from an SAP system. The IDOC being received has the version number less than the SAP SYSREL.|  
|RFCServer|Demonstrates how to receive an RFC server call from the SAP system.|  
|SAPTransaction|Demonstrates how to perform transactions in an SAP system using.|  
|tRFCClient|Demonstrates how to make tRFC client calls on an SAP system.|  
  
## WCF Service Model Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|SapIdocStringClientSM|Demonstrates how to send an IDOC to an SAP system by invoking the SendIdoc operation.|  
|SapRfcServerSM|Demonstrates how to receive an RFC server call from an SAP system.|  
|SapBapiTxClientSM|Demonstrates how to invoke BAPIs inside a transaction on an SAP system.|  
|SapTrfcClientSM|Demonstrates how to invoke tRFC client calls on an SAP system.|  
  
## WCF Channel Model Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|SapIdocReceiveCM|Demonstrates how to receive IDOCs from an SAP system|  
|SapRfcServerCM|Demonstrates how to receive an RFC server call from the SAP system.|  
  
## Data Provider for SAP Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|sap ado|Demonstrates how to use the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].|  
  
## Migration Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|SAP_RFC_Migration|Demonstrates how to use a BizTalk project created using the previous version of the SAP adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The BizTalk project contains an orchestration to invoke the SD_RFC_CUSTOMER_GET RFC.|  
|SendIDOC_Migration|Demonstrates how to use a BizTalk project created using the previous version of the SAP adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The BizTalk project contains an orchestration to send an IDOC to an SAP system.|  
|ReceiveIDOC_Migration|Demonstrates how to use a BizTalk project created using the previous version of the SAP adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The BizTalk project contains an orchestration to invoke the receive an IDOC from an SAP system.|  
  
## See Also  
[Develop your SAP applications](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)