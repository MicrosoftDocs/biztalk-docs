---
title: "POP3 Transport Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.pop3.receive"
helpviewer_keywords: 
  - "polling interval [receive adapters]"
  - "receive locations, POP3 adapters"
  - "POP3 adapters, receive locations"
  - "properties, POP3 adapters"
  - "POP3 adapters, properties"
  - "POP3 adapters, polling interval"
ms.assetid: 7a8f6bc5-2af2-4fd7-abbc-865f9995d60a
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# POP3 Transport Properties Dialog Box
Use the **POP3 Transport Properties** dialog box to configure the receive location for the POP3 adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Apply MIME decoding**|Specify whether or not to apply MIME decoding to messages that are received by the POP3 adapter.<br /><br /> Default value: True<br /><br /> Type: Boolean **Important:**  If this value is set to False then the POP3 adapter will submit the complete e-mail body including message headers to BizTalk Server.|  
|**Body Part Content Type**|Specify the MIME Body Part of the incoming e-mail message to be submitted to BizTalk Server.<br /><br /> Type: String **Note:**  The POP3 adapter is designed to recognize the Body Part Content Types that are defined in RFC 2046. <br /><br /> For more information about the POP3 adapter, see the topics in See Also.|  
|**Body Part Index**|Specify the Body Part Index of the incoming e-mail messages to submit to BizTalk Server.<br /><br /> Default value: 0<br /><br /> Type: Long<br /><br /> For more information about the POP3 adapter, see the topics in See Also.|  
|**Mail Server**|Required. Specify the POP3 mail server that houses the mailbox that will be polled by the POP3 adapter.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Port**|Specify the TCP Port to use for the connection to the specified POP3 server.<br /><br /> Default value: 0<br /><br /> Type: Long **Note:**  A value of 0 indicates to use the default POP3 port of 110 if Use SSL is False or port 443 if Use SSL is True.|  
|**Authentication Scheme**|Specify the type of authentication to use when connecting to the POP3 server.<br /><br /> Options:<br /><br /> -   Basic<br />-   Digest<br />-   SPA<br /><br /> Type: String **Note:**  When using SPA authentication, the user name must be specified with one of the following formats: Domain accounts must be entered with the syntax \<domain name>\\<username\> Local accounts must be entered with the syntax \<machine name>\\<username\>|  
|**Password**|Specify the password used to authenticate to the POP3 mailbox.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Use SSL**|Specify whether to connect to the POP3 server over SSL (TCP Port 443).<br /><br /> Default value: False<br /><br /> Type: Boolean|  
|**User Name**|Required. This is the user name used to access the specified mailbox.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Error Threshold**|Specify the maximum number of network or protocol errors to wait before shutting down the adapter.<br /><br /> Default value: 10<br /><br /> Type: Long<br /><br /> Minimum value: 0|  
|**Polling Interval**|Specify the interval between attempts to retrieve messages from the POP3 server.<br /><br /> Default value: 5<br /><br /> Type: Long<br /><br /> Minimum value: 2<br /><br /> Maximum value: 120|  
|**Polling Interval Unit**|Specify the unit of measure to be used for the Polling Interval.<br /><br /> Options:<br /><br /> -   Seconds<br />-   Minutes<br />-   Hours<br />-   Days<br />-   Default value: Minutes<br /><br /> Type: String|  
  
## See Also  
 [How to Configure a POP3 Receive Handler](../core/how-to-configure-a-pop3-receive-handler.md)   
 [What Is the POP3 Adapter?](../core/what-is-the-pop3-adapter.md)