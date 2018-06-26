---
title: "What Is the POP3 Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "POP3 adapters, availability"
  - "authenticating, POP3 adapters"
  - "POP3 adapters, data duplication"
  - "data duplication"
  - "POP3 adapters, receive adapters"
  - "high availability, POP3 adapters"
  - "POP3 adapters, supported platforms"
  - "POP3 adapters, authenticating"
  - "POP3 adapters, algorithims"
  - "receive adapters, POP3 adapters"
ms.assetid: 05e9598b-cdfe-4216-b6bf-1b84f8ddfeae
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the POP3 Adapter?
This section describes the POP3 receive adapter.  
  
## POP3 Receive Adapter  
 The POP3 receive adapter enables you to move data from a POP3-enabled mailbox to BizTalk Server.  
  
 The key features of the POP3 receive adapter are:  
  
-   Pulling files from the POP3 server mailbox on demand.  
  
-   Running polls based on a configurable schedule.  
  
-   Polling the POP3 server mailbox and sending data directly to BizTalk Server.  
  
-   Specifying the POP3 server mailbox as an IP address or host name, port, user name, and password.  
  
-   Ability to download e-mail from mail servers that require Secure Sockets Layer (SSL) connections.  
  
-   Guaranteed file delivery.  
  
-   Implicit MIME processing. It is not necessary to use a MIME decoder in a receive pipeline when using the POP3 adapter.  
  
## POP3 Adapter Supported Platforms  
 The POP3 adapter is designed to work with any POP3 servers that conform to the following RFCs:  
  
- **RFC 1939.** Post Office Protocol Version 3 (see [http://go.microsoft.com/fwlink/?LinkId=58808](http://go.microsoft.com/fwlink/?LinkId=58808))  
  
- **RFC 1734.** POP3 AUTHentication command (see [http://go.microsoft.com/fwlink/?LinkId=58809](http://go.microsoft.com/fwlink/?LinkId=58809))  
  
- **RFC 2045.** Multipurpose Internet Mail Extensions (MIME) Part One: Format of Internet Message Bodies (see [http://go.microsoft.com/fwlink/?LinkId=58810](http://go.microsoft.com/fwlink/?LinkId=58810))  
  
- **RFC 2046.** Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types (see [http://go.microsoft.com/fwlink/?LinkId=58811](http://go.microsoft.com/fwlink/?LinkId=58811))  
  
- **RFC 2047.** MIME (Multipurpose Internet Mail Extensions) Part Three: Message Header Extensions for Non-ASCII Text (see [http://go.microsoft.com/fwlink/?LinkId=58812](http://go.microsoft.com/fwlink/?LinkId=58812))  
  
  The POP3 adapter was tested extensively against Microsoft Exchange Server 2003.  
  
## Considerations for Preventing Data Duplication When Using the POP3 Adapter  
 The POP3 adapter is not a transactional adapter and therefore is subject to processing multiple copies of the same message, potentially causing data duplication. It is possible that the POP3 adapter will deliver duplicate copies of a message in the following scenarios:  
  
-   The POP3 adapter always deletes e-mails from the mailbox that it is configured to monitor after the e-mail has been successfully submitted to BizTalk Server for processing. If the POP3 adapter retrieves an e-mail from a mailbox, submits the e-mail to BizTalk Server for processing, and fails to delete the e-mail from the mailbox, the e-mail will be resubmitted to BizTalk Server the next time that the POP3 adapter polls the mailbox.  
  
-   If multiple instances of the POP3 adapter in separate BizTalk Host instances are monitoring the same mailbox simultaneously and the POP3 server allows multiple concurrent connections to its mailboxes, then the adapter may deliver duplicate copies of messages.  
  
## High Availability for the POP3 Adapter  
 Some POP3 servers permit multiple concurrent connections to a given mailbox. If more than one instance of the POP3 adapter is configured to retrieve mail from a mailbox on such a POP3 server then data duplication can occur. Therefore you should configure only one instance of the POP3 adapter to retrieve mail from a mailbox that permits multiple concurrent connections.  
  
 To provide fault tolerance for the POP3 adapter in this scenario, a single POP3 adapter receive handler should be configured to run in a clustered BizTalk Host. For more information see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
## Authentication Warnings When Multiple Instances of the POP3 Adapter Connect to the Same Mailbox  
 BizTalk Server may be configured to have more than one instance of the POP3 adapter retrieve mail from the same mailbox. In such a case, it is possible that authentication warnings may be generated in the BizTalk Server Application log because of the locking mechanism employed by some POP3 servers. These warnings will have no impact on the POP3 adapter functionality and can be safely ignored in this scenario.  
  
## Encrypted Messages Received by the POP3 Adapter that are sent to the Suspended Queue may be Viewable in Clear Text  
 You can configure the POP3 adapter to decrypt digitally encrypted e-mails. This is done by setting the **Apply MIME Decoding** property to **True** for receive locations that use the POP3 adapter. If the POP3 Adapter receives a digitally encrypted e-mail and the **Apply MIME Decoding** property for the receive location is set to **True** then the POP3 adapter attempts to decrypt the e-mail as follows:  
  
- The POP3 Adapter searches for a private certificate that matches the public certificate used to encrypt the e-mail. The private certificate must be in the Personal certificate store of the server that is running the host instance that the POP3 receive handler is bound to.  
  
- If the POP3 Adapter locates a corresponding private certificate, it uses the private certificate to decrypt the e-mail message.  
  
- The e-mail is decrypted and persisted to the BizTalk MessageBox.  
  
  If a message is suspended after being decrypted and persisted to the BizTalk MessageBox, the contents of the message will be visible in clear text in the BizTalk suspended queue.  
  
  If you need to prevent the display of secure message text in the suspended queue, follow these steps:  
  
- Set the **Apply MIME Decoding** property to **False** for receive locations that use the POP3 adapter and decrypt the message in a pipeline with the SMIME pipeline component.  
  
  > [!NOTE]
  >  This approach will prevent you from being able to promote e-mail specific properties to the message context.  
  
- If you need to promote e-mail specific properties to the message context and ensure that encrypted messages remain encrypted if they are routed to the suspended queue, follow these steps:  
  
  -   Check the option to **Enable routing for failed messages** on the receive port that houses the receive location(s) that use the POP3 adapter.  
  
  -   Create an orchestration to subscribe to messages that fail delivery to the receive port that houses the receive location(s) that use the POP3 adapter.  
  
  -   Configure the orchestration with a send port that encrypts the message in a pipeline using the SMIME pipeline component.  
  
  -   Configure the orchestration with a suspend shape to suspend the orchestration instance and the message.  
  
  -   Build and deploy the orchestration, bind the deployed orchestration to the appropriate receive port.  
  
## Maximum Message Size Supported by the POP3 Adapter  
 The POP3 adapter has been tested with and supports receiving messages up to 50 MB in size.  
  
## See Also  
 [POP3 Adapter](../core/pop3-adapter.md)