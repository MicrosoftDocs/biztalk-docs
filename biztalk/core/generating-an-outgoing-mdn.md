---
title: "Generating an Outgoing MDN | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12d7da1c-0d3c-42d4-9388-29f499353d13
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generating an Outgoing MDN
The AS2 receive pipelines generate an MDN (Message Disposition Notification) response for an incoming message. This is performed by the EDI Disassembler pipeline component in the AS2EDIReceive receive pipeline (in response to an EDI-encoded message) or the AS2 Disassembler pipeline component in the AS2Receive receive pipeline (in response to a non-EDI-encoded message).  
  
## When and How an MDN is Generated  
 An MDN is normally generated based upon the AS2 headers in the original AS2 message, as follows:  
  
- An MDN will be sent if the Disposition-Notification-To header is present in the AS2 message.  
  
- If the Disposition-Notification-To header and the Receipt-Delivery-Option header are present in the message, the MDN will be sent asynchronously. It will be sent to the URL in the Receipt-Delivery-Option header, over a different connection than the original message.  
  
- If the Disposition-Notification-To header is present in the message, but the Receipt-Delivery-Option header is not present in the message, the MDN will be sent synchronously over the same connection as the original message.  
  
  The Disassembler creates the AS2-From header in the MDN from the AS2-To header in the received AS2 message, and it creates the AS2-To header in the MDN from the AS2-From header in the received AS2 message.  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to override these settings, specifying whether an MDN will be generated and how it will be generated based upon a party's AS2 agreement properties. You override the AS2 header settings in the message using the **Use agreement settings for validation and MDN instead of message header** property in the one-way AS2 agreement tab of the **Agreement Properties** dialog box. This property enables you to send an MDN even if the AS2 header does not call for one, or to send the MDN asynchronously when the AS2 header specifies a synchronous connection.  
  
  If you set the **Use agreement settings for validation and MDN instead of message header** property, the values in the **Request MDN** section of the **Sender MDN Settings** page in the one-way AS2 agreement tab of the **Agreement Properties** dialog box will be used for the MDN, as follows:  
  
- An MDN will be sent if the **Request MDN** property is selected.  
  
- If the **Request MDN** property is selected, and the **Request asynchronous MDN** property is selected, the MDN will be sent asynchronously. The MDN will be sent to the URL that the **Receipt-Delivery-Option (URL)** property is set to, over a different connection than the original message.  
  
- If the **Request MDN** property is selected, but the **Request asynchronous MDN** property is not selected, the MDN will be sent synchronously over the same connection as the original message.  
  
  If the **Use agreement settings for validation and MDN instead of message header** property is set, the AS2-From property in the message header will be used in generating the MDN, but AS2-To will be taken from the agreement properties, and the pipeline will sign the MDN according to the **Request Signed MDN** property. The AS2 headers correspond to the agreement properties as follows:  
  
|Agreement Property|AS2 Header in the Message|  
|------------------------|-------------------------------|  
|Generate MDN|Disposition-Notification-To|  
|Sign MDN|Signed-Receipt-Protocol|  
|Receipt-Delivery-Option|Receipt-Delivery-Option|  
  
 If an MDN is enabled, the receive pipeline will promote the following context properties:  
  
- `EdiIntAS.DispositionMode`  
  
- `EdiIntAS.DispositionType`  
  
  Both of these context properties must be promoted in order for the MDN to be generated. For more information about these context properties, see [AS2 Context Properties](../core/as2-context-properties.md).  
  
  If the configuration settings and the headers in the incoming message are inconsistent, the pipeline will generate a negative MDN.  
  
  If the MDN is requested in the agreement properties, the receive pipeline will attempt to send an MDN even if an error occurs in AS2 processing.  
  
## How the Receive Pipeline Processes a Generated MDN  
 If an MDN is generated according to the above rules, the AS2EDIReceive or AS2Receive receive pipeline will process the MDN as follows:  
  
-   Makes a copy of the MDN (in wire format), and stores it in the non-repudiation database, if enabled in the one-way AS2 agreement properties.  
  
-   Performs MIME processing, including applying a digital signature, if enabled in the one-way AS2 agreement properties.  
  
-   Calculates the MIC (Message Integrity Check) for the AS2 message payload and appends it to the Received-content-MIC extension field of the MDN. The algorithm to be applied for the MIC is determined by the signed-receipt-micalg header of the incoming message or the **Signing Algorithm** property on the **Sender MDN Settings** page of the one-way agreement tab of the **Agreement Properties** dialog box (when the inbound message properties are overridden). It can be either SHA1 or MD5. The value of the algorithm is also included in the MDN.  
  
-   Makes correlation entries in the non-repudiation database.  
  
-   Makes a copy of the MDN message.  
  
-   If the MDN is to be transmitted synchronously, the pipeline sets the `EdiIntAS.IsAS2AsynchronousMDN` property to False; if asynchronously, it sets the property to True.  
  
-   If the MDN is to be transmitted synchronously, the AS2Send send pipeline associated with the two-way receive port will pick up the MDN based upon the `EdiIntAS.IsAS2AsynchronousMDN` property (set to False) and the correlation tokens.  
  
    > [!NOTE]
    >  You can also set up a send port that subscribes to the outgoing synchronous MDN. To do so, set the send port filter to `EdiIntAS.IsAS2MdnResponseMessage==True`.  
  
-   If the MDN is to be transmitted asynchronously, the receive pipeline routes the MDN to the MessageBox. You must set up a send port to subscribe to the MDN, setting the send port filter to `IsAS2AsynchronousMdn==True`. The AS2Send send pipeline picks up the message based upon that property and the correlation tokens. If the send port is dynamic, it will route the MDN based to the address in the Receipt-Delivery-Notification line in the header of the message. If the send port is static, it will route the message based upon Transport URI property of the send port.  
  
## MDN Generation Rules  
 The following rules apply to MDN generation:  
  
-   When a message sender specifically requests a signed receipt, but there is error in processing the contents of the message, the message receiver must still return a signed receipt, even though the transaction itself may not be valid. The reason for the error in processing the contents of the message must be set in the "disposition-field".  
  
-   When the request for the MDN receipt explicitly specifies that the receipt be signed, but the receiver of the original message cannot support either the requested protocol format or the requested MIC algorithm, then either a signed or unsigned receipt should be returned.  
  
-   When a signature is not explicitly requested, or if the signed receipt request parameter is not recognized by the agreement for the receiving party, then the receiving party may return an unsigned receipt, a signed receipt, or no receipt.  
  
## MIC Generation  
 When an MDN is required, the receiver of the original message generates an MIC (Message Integrity Check) and adds it to the MDN. When the EDI interchange is part of a multi-part MIME content-type, the MIC must be calculated across the entire multi-part content, including the EDI interchange and the MIME headers. For encrypted, unsigned messages, the MIC to be returned is calculated on the decrypted MIME header and content. For unsigned, unencrypted messages, the MIC must be calculated over the message contents without the MIME headers.  
  
## See Also  
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)