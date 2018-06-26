---
title: "SAP adapter samples | Microsoft Docs"
description: mySAP WCF adapter samples that can be used with BizTalk Server, WCF service model, WCF channel model, and the Data Provider for SAP
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the SAP adapter
Samples for [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] are categorized into:  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  

- WCF service model samples  

- WCF channel model samples  

- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] samples  


 The samples are available at [BizTalk Adapter Pack 2010: SAP adapter samples](https://www.microsoft.com/download/details.aspx?id=1314). 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]

 The following list describes the samples.

## BizTalk Server samples  

|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|IDOCSend|Demonstrates how to send an IDOC to an SAP system.|  
|ReceiveIDOC|Demonstrates how to receive an IDOC from an SAP system.|  
|ReceiveIDOC_SYSREL|Demonstrates how to receive an IDOC from an SAP system. The IDOC being received has the version number less than the SAP SYSREL.|  
|RFCServer|Demonstrates how to receive an RFC server call from the SAP system.|  
|SAPTransaction|Demonstrates how to perform transactions in an SAP system using.|  
|tRFCClient|Demonstrates how to make tRFC client calls on an SAP system.|  

## WCF service model samples   

|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|SapIdocStringClientSM|Demonstrates how to send an IDOC to an SAP system by invoking the SendIdoc operation.|  
|SapRfcServerSM|Demonstrates how to receive an RFC server call from an SAP system.|  
|SapBapiTxClientSM|Demonstrates how to invoke BAPIs inside a transaction on an SAP system.|  
|SapTrfcClientSM|Demonstrates how to invoke tRFC client calls on an SAP system.|  

## WCF channel model samples  

|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|SapIdocReceiveCM|Demonstrates how to receive IDOCs from an SAP system|  
|SapRfcServerCM|Demonstrates how to receive an RFC server call from the SAP system.|  

## Data Provider for SAP samples  

| Sample Directory Name |                                             Description                                              |
|-----------------------|------------------------------------------------------------------------------------------------------|
|        sap ado        | Demonstrates how to use the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]. |

## See Also  
[Develop your SAP applications](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)