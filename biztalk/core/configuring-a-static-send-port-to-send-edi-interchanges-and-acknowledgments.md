---
description: "Learn more about: Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments"
title: "Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b432c5e-ea0c-4174-bb4a-958b061c1827
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments
To send an EDI acknowledgment or interchange, you can use either a static one-way send port or a static solicit-response (two-way) send port.  
  
-   Create a one-way send port if you will also create a one-way receive port to receive EDI acknowledgments (if enabled).  
  
-   Create a solicit-response send port to send EDI interchanges and receive EDI acknowledgments (if enabled) over the associated receive pipeline.  
  
## Configuring a Static One-Way Send Port  
 To create a static one-way send port to send EDI interchange and acknowledgments, use the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port type|Static One-Way|  
|**Send Port Properties: General**|Transport Type|Can be many types, including FILE, FTP, HTTP, MQSeries, MSMQ, SMTP, SOAP, SQL, WCF types, and Windows SharePoint Services.|  
|**Send Port Properties: General**|Send handler|BizTalkServerApplication|  
|**Send Port Properties: General**|Send pipeline|EdiSend|  
|**Transport Properties: Authentication (for FILE transport type)**|Use these credentials when host does not have access to network share (with User name and Password)|Set if authentication is required.|  
|**Send Port Properties: Filters**|Property|BTS.MessageType<br /><br /> Note:<br /><br /> You can also use BTS.ReceivePortName or other promoted properties.|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|**Using BTS.MessageType for interchanges:**<br /><br /> - **For X12**: `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, or<br /><br /> - **For EDIFACT**: `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`<br /><br /> **Using BTS.MessageType for ACKs**:<br /><br /> -                     **For X12**: `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, or<br /><br /> -                     **For X12**: `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, or<br /><br /> -                     **For EDIFACT**: `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## Configuring a Static Solicit-Response Send Port  
 To create a static solicit-response (two-way) send port to send EDI interchange and acknowledgments, use the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port type|Static solicit-response|  
|**Send Port Properties: General**|Transport Type|Can be many types, including HTTP, MQSeries, MSMQ, SOAP, SQL, and WCF types. Cannot be FILE, FTP, SMTP, or Windows SharePoint Services.|  
|**Send Port Properties: General**|Send handler|BizTalkServerApplication|  
|**Send Port Properties: General**|Send pipeline|EdiSend|  
|**Send Port Properties: General**|Receive pipeline|EdiReceive|  
|**Transport Properties: Authentication (for HTTP transport type)**|Use these credentials when host does not have access to network share (with User name and Password)|Set if authentication is required.|  
|**Send Port Properties: Filters**|Property|BTS.MessageType<br /><br /> Note:<br /><br /> You can also use BTS.ReceivePortName or other promoted properties.|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|**Using BTS.MessageType for interchanges:**<br /><br /> -                     **For X12**: `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, or<br /><br /> -                     **For EDIFACT**: `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`<br /><br /> **Using BTS.MessageType for ACKs**:<br /><br /> -                     **For X12**: `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, or<br /><br /> -                     **For X12**: `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, or<br /><br /> -                     **For EDIFACT**: `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## Setting Agreement Properties  
 After creating the send port, you need to set the agreement properties required for the send pipeline to function. These properties are set in various pages of the **Agreement Properties** dialog box.  
  
## See Also  
 [Configuring Ports for an EDI Solution](../core/configuring-ports-for-an-edi-solution.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)
