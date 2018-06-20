---
title: "Configuring a Receive Port for Messages over AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01d4d897-d12b-4de4-a86b-e6d2718470c2
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Receive Port for Messages over AS2
To receive an AS2 message with an EDI or non-EDI payload, create an HTTP receive port to receive the message and return a response back to the party.  

 If the MDN will be returned synchronously, the receive port must be a two-way request-response receive port. A receive location in the receive port will receive the AS2 message, while the send port associated with the two-way receive port will send the synschronous MDN.  

 If the MDN will be returned asynchronously, the receive port can be a one-way receive port, because the MDN must be returned over a separate dynamic send port. An HTTP response will be returned by the receive port, whether it is a one-way or two-way port. If you set up a two-way receive port to receive an AS2 message, while returning an asynchronoius MDN, the HTTP response will be returned over the send port of the two-way receive location.  

> [!NOTE]
>  The two-way receive port used to receive AS2 messages should not be used to receive MDN messages. MDN messages should be received on a static one-way receive port. Using a request/response receive port for an MDN would prevent a 200OK message from being returned in response to the incoming MDN, thereby causing unnecessary retries of the MDN transmission.  

 Create the receive port with the following configuration:  


|                 Location                 |                Property                |                                                                                                                                                                                                                                                                                           Setting                                                                                                                                                                                                                                                                                           |
|------------------------------------------|----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **Receive Port Properties: General**   |               Port type                |                                                                                                                                                                                                                                                                                      Request-Response                                                                                                                                                                                                                                                                                       |
| **Receive Location Properties: General** |             Transport Type             |                                                                                                                                                                                                          HTTP **Note:**  Only the HTTP adapter can be used for transporting EDIINT/AS2-encoded messages. This transport will not work with an adapter other than the HTTP adapter.                                                                                                                                                                                                          |
| **Receive Location Properties: General** |            Receive handler             |                                                                                                                                                                                                                                                                                  BizTalkServerIsolatedHost                                                                                                                                                                                                                                                                                  |
| **Receive Location Properties: General** |            Receive pipeline            | -   AS2EdiReceive (if the payload is EDI-encoded)<br />-   AS2Receive (if the payload is not EDI-encoded) **Note:**  When using the AS2EdiReceive pipeline, you must add the user account that the BizTalk Isolated Host Instance process is running under to the BizTalk Application Users group. The AS2EdiReceive pipeline executes in the BizTalk Isolated Host Instance process. The AS2EdiReceive pipeline accesses the SSO store, which requires that the user is in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Users group. |
| **Receive Location Properties: General** |             Send pipeline              |                                                                                                                                                                                                                                                                                           AS2Send                                                                                                                                                                                                                                                                                           |
|      **HTTP Transport Properties**       | Virtual directory plus ISAPI extension |                                                                                                                                                                                                                                                                      /\<name of virtual directory\>/BTSHTTPReceive.dll                                                                                                                                                                                                                                                                      |
|      **HTTP Transport Properties**       |  Request-Response Return content type  |                                                                                                                                                                                                                                                                                          text/xml                                                                                                                                                                                                                                                                                           |

## Functionality of the Receive Location in Synchronous and Asynchronous Modes  
 The two-way receive port does the following to receive and process an EDI/AS2 message and return a response:  

-   Receive the AS2 message over HTTP.  

-   Process the AS2 message using the AS2EDIReceive receive pipeline (for EDI-encoded messages) or the AS2Receive receive pipeline (for messages that are not encoded in EDI). For more information on this process, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).  

-   Set the following context properties on the received message:  

    -   `IsAS2PayloadMessage == True` (because it is a payload message)  

    -   `IsEmptyMDNResponse == False` (because it is not an empty MDN)  

-   If the message is EDI-encoded, disassemble the EDI file, generate XML files, and drop them into the MessageBox. Set the context property of `BTS.MessageType` for each XML file to the schema name with namespace.  

-   If the message is not EDI-encoded, drop the message in its native format into the MessageBox.  

-   Generate the MDN file, if enabled, using the AS2EdiReceive receive pipeline. For more information on this process, see [Generating an Outgoing MDN](../core/generating-an-outgoing-mdn.md). Set the following context properties on the message:  

    -   `EdiIntAS.IsAS2AsynchronousMdn == False` (if in synchronous mode)  

    -   `EdiIntAS.IsAS2AsynchronousMdn== True` (if in asynchronous mode)  

-   If in synchronous mode, send the MDN file, if enabled, using the AS2Send send pipeline. For more information on this process, see [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).  

-   If in asynchronous mode, route the MDN file, if enabled, to the MessageBox (for a separate dynamic send port to pick it up and send it).  

-   If in asynchronous mode, generate an empty MDN in addition to the complete MDN that it returns asynchronously. Set the following context properties on the message:  

    -   `IsAS2PayloadMessage == False`  

    -   `IsEmptyMDNResponse == True`  

-   If in asynchronous mode, return the HTTP response to the original sender over the HTTP connection between the receive port and the sending party, which closes that connection. This is necessary because the synchronous connection is not closed by the complete MDN.  

-   Generate an acknowledgment message, if enabled, and drop it into the MessageBox. Set the context property of `BTS.MessageType` to the acknowledgment control schema.  

## See Also  
 [Configuring Ports for an AS2 Solution](../core/configuring-ports-for-an-as2-solution.md)   
 [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md)   
 [Generating an Outgoing MDN](../core/generating-an-outgoing-mdn.md)   
 [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md)