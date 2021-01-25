---
description: "Learn more about: Configuring a Dynamic Send Port to Send EDI Interchanges and Acknowledgments"
title: "Configuring a Dynamic Send Port to Send EDI Interchanges and Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a124059c-c29c-4a7f-a8a3-13dffc09ae5c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Dynamic Send Port to Send EDI Interchanges and Acknowledgments
To send an EDI acknowledgment or interchange, you can use either a static send port or a dynamic send port. A dynamic send port enables you to send an interchange to any one of multiple destinations, because it resolves the agreement and determines the destination address based upon the value in the DestinationPartyName context property.  
  
> [!NOTE]
>  If you are sending an EDI interchange that is based upon an XML message received, and you are using a passthrough receive pipeline to receive that application, you will have to promote the DestinationPartyName context property. For more information, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
> [!NOTE]
>  If the dynamic send port will be sending an acknowledgment, the DestinationPartyName context property will already be promoted because the EDI Disassembler in the port that received the interchange populates the DestinationPartyName property on the acknowledgment.  
  
 To create a one-way dynamic send port, use the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port type|Dynamic One-Way|  
|**Send Port Properties: General**|Send handler|BizTalkServerApplication|  
|**Send Port Properties: General**|Send pipeline|EdiSend|  
|**FILE Transport Properties: Authentication**|Use these credentials when host does not have access to network share (with User name and Password)|Set if authentication is required.|  
|**Send Port Properties: Filters**|Property|BTS.MessageType|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|**For interchanges**:<br /><br /> - `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, or<br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`,or<br /><br /> **For ACKs**:<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, or<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, or<br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## Setting Agreement Properties  
 After creating the send port, you need to set the agreement properties required for the send pipeline to function. These properties are set in various pages of the **Agreement Properties** dialog box.  
  
## See Also  
 [Configuring Ports for an EDI Solution](../core/configuring-ports-for-an-edi-solution.md)
