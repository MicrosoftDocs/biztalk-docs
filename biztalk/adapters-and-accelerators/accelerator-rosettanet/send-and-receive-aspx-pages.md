---
title: "Send and Receive ASPX Pages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BTARN, ASPX pages"
  - "ASPX pages, initiator"
  - "HTTP adapters"
  - "connections, HTTP adapters"
  - "connections, single-action"
  - "ASPX pages, responder"
  - "single-action connections"
  - "RNIFSend.aspx"
  - "connections, asynchronous"
  - "ASPX pages, about ASPX pages"
  - "double-action connections"
  - "connections, synchronous"
  - "connections, double-action"
  - "ASPX pages"
  - "HTTP adapters, connections"
  - "asynchronous connections"
  - "RNIFReceive.aspx"
  - "synchronous connections"
ms.assetid: 21e52390-35d8-44b1-a5cd-1cd60cfe6e61
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send and Receive ASPX Pages
The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] ASPX pages are the direct interfaces between [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] and the Internet. The two ASPX pages are the receive page (RNIFReceive.aspx) and the send page (RNIFSend.aspx). Each ASPX page is an extension to the corresponding [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline. The pipeline requires the ASPX page to handle RosettaNet Implementation Framework (RNIF) headers. The pipeline performs most of the HTTP processing; however, each ASPX page performs the HTTP processing of the RNIF headers. The pages augment the functionality in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] HTTP adapter.  
  
 Each ASPX page is an ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web application with no user interface. They use ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web security to ensure a secure connection with external parties. They provide a layer in which you can implement fault tolerance, scalability, and highly available services.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs an RNIFSend.aspx page and an RNIFReceive.aspx page on each deployment of [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. When the initiator or responder exchanges messages with the trading partner, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses the ASPX pages to send messages to, or receive messages from, the partner URL. If both the initiator and the responder use [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the two ASPX pages on the initiator exchange messages with the two ASPX pages on the responder. For more information, see the "How Initiator and Responder ASPX Pages Interact" subsection below.  
  
## Send ASPX Page  
 The RNIFSend.aspx page receives a message from the BizTalk HTTP adapter. It creates and adds RNIF headers to the message, and then sends the message to the partner over the Internet. The HTTP adapter calls RNIFSend.aspx with the following command:  
  
```  
http://localhost:<port number>/RNIFSend.aspx?<query string>  
```  
  
 The query string includes the following data that the send page needs to send the message to the partner, and the data that the partner must have to process the message:  
  
- The trading-partner URL: http://www.\<*address*\>.com/RNIFReceive.aspx  
  
- The response type: sync or async  
  
- The RNIF version: 1.1 or 2.0.  
  
  The BizTalk HTTP adapter sends a MIME message produced by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline to the initiator RNIFSend.aspx page. RNIFSend.aspx processes the message as follows:  
  
1.  The send page performs validation on the message.  
  
2.  The send page creates a Multipurpose Internet Mail Extensions (MIME) header based upon the content type, the length, the ID, and the MIME version. It adds the MIME header, and upper and lower MIME boundaries, to the message.  
  
3.  For RNIF 2.01, the send page sets properties of the HTTP header as follows:  
  
    1.  It sets the X-RN-Version property to the version entered in the Version property of the process configuration settings.  
  
    2.  It sets the X-RN-ResponseType property to either sync or async, depending upon the setting of the IsSynchronous property in the process configuration settings.  
  
    3.  It sets the Content-Length property to the size of the full message.  
  
4.  Using an HTTP Post, the send page sends the message to the partner's destination URL, as set in the Action URL or Signal URL settings in the trading partner agreement.  
  
5.  The send page waits for the HTTP response. When it receives the response, it routes it to the HTTP adapter.  
  
6.  If the connection is asynchronous, the send page closes the connection, and its processing is complete.  
  
7.  If the connection is synchronous, the send page keeps the connection open for a returned message. After it receives the message, it performs the same processing that an RNIFReceive.aspx page performs on a received message, sends the received message to the HTTP adapter, and then closes the connection.  
  
## Receive ASPX Page  
 The RNIFReceive.aspx page receives an HTTP message from the partner over the Internet. It processes, validates, and then removes the RNIF headers, and submits the message to the HTTP adapter. The message received by the receive page must be RNIF HTTP transport-compliant. The receive page processes messages as follows:  
  
1.  The responder RNIFReceive.aspx page receives the message from the initiator. The message contains the MIME header and upper and lower boundaries.  
  
2.  The receive page validates the MIME header.  
  
3.  The receive page removes the MIME header and boundaries from the message.  
  
4.  The receive page posts the message to the HTTP adapter using the HTTP receive location. The receive page receives an HTTP response, and returns the HTTP response to the send page of the initiator.  
  
5.  If the connection is asynchronous, the receive page closes the connection.  
  
6.  If the connection is synchronous, the receive page keeps the connection open, waiting for a returned message.  
  
7.  After it receives the returned message from the HTTP adapter, the receive page performs the same processing that an RNIFSend.aspx page does, and sends the returned message to the initiator send page. After it receives the HTTP response, it closes the connection.  
  
## How Initiator and Responder ASPX Pages Interact  
 If both the initiator and the responder use [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the four ASPX pages on the initiator and responder interact differently depending on whether the connections are asynchronous or synchronous, and whether the messages are single-action or double-action. The following subsections describe the complete set of interactions.  
  
 **Double-Action Asynchronous**  
  
 This scenario involves four separate HTTP connections, one for each step:  
  
1. The initiator send page sends the action request message to the responder receive page.  
  
   > [!NOTE]
   >  Steps 2 and 3 below may occur in the reverse order, depending upon system load.  
  
2. The responder send page sends a request signal message to the initiator receive page.  
  
3. The responder send page sends an action response message to the initiator receive page.  
  
4. The initiator send page sends a response signal message to the responder receive page.  
  
   **Single-Action Asynchronous**  
  
   This scenario involves two separate HTTP connections, one for each step. Note that this scenario consists of step 1 and 2 of the double-action asynchronous scenario.  
  
5. The initiator send page sends the action request message to the responder receive page.  
  
6. The responder send page sends a request signal message to the initiator receive page.  
  
   **Double-Action Synchronous**  
  
   This scenario involves one HTTP connection:  
  
7. The initiator send page sends the action request message to the responder receive page.  
  
8. The responder receive page sends an action response message (or an exception, if there is a problem) to the initiator send page on the same connection used in step 1.  
  
   **Single-Action Synchronous**  
  
   This scenario involves one HTTP connection:  
  
9. The initiator send page sends the action request message to the responder receive page.  
  
10. The responder receive page sends a request signal message (or an exception, if there is a problem) to the initiator send page on the same connection.  
  
## See Also  
 [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)   
 [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)   
 [BTARN Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)