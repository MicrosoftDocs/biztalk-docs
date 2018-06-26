---
title: "Configuring the Sending and Receiving of EDI Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db1c9f7-bafa-4659-a3c4-0faa56606081
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the Sending and Receiving of EDI Acknowledgments
To configure the sending of an EDI acknowledgment in response to a received interchange, you need to do the following:  
  
-   Enable the acknowledgment in the agreement that the received interchange resolved to. By doing this, you declare that the party that sent the interchange expects an acknowledgement.  
  
-   If the acknowledgement needs to be send back with specific properties set, such as CR LF enabled, separator characters to be different, etc., set those properties in the other one-way agreement tab. By doing this, you configure how the party sends back the acknowledgement.  
  
    > [!NOTE]
    >  If an interchange resolved to an agreement defined in the **PartyA->PartyB** tab, the properties related to how the acknowledgement should be generated are configured in the **PartyB->PartyA** tab. This is required because the acknowledgement context properties for the sender and receiver qualifiers are set to the opposite of the values you specified in the **PartyA->PartyB** tab. For example, if sender and receiver identifiers are set to THEM and US in the agreement to which the interchange message resolved to, the sender and receiver context properties will be set to US and THEM in the acknowledgement. Typically, the other one-way agreement tab would also have the sender and receiver identifiers set to US and THEM respectively. Hence, the acknowledgement message would resolve to that agreement and the properties setting will be picked. So, if you want to have the acknowledgement to use different element separators or if you want to have the acknowledgement to use CR LF, specify the properties in the **PartyB->PartyA** tab.  
  
     Conceptually, the properties for the acknowledgement will be picked from any one-way agreement tab that has the same sender and receiver qualifiers as set in the acknowledgement’s context properties. However, for ease of practical use, you would typically set this in the other one-way agreement tab of the agreement that you created to which the interchange would have resolved.  
  
-   If you are a party that is sending an EDI acknowledgement back to the party that sent the original interchange, set up a one-way send port to pick up the acknowledgment and send or a two-way receive port to send the acknowledgment. For more information, see [Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md).  
  
-   If you are a party that is expecting an EDI acknowledgement, set up a two-way send port or a one-way receive port to receive the acknowledgment. For more information, see [Configuring a Port to Receive EDI Messages and Acknowledgments](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).  
  
-   The BizTalk EDI Application contains the control schemas. As a result, the application containing your EDI solution must contain a reference to BizTalk EDI Application. For more information, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To request an acknowledgment for the party that sent the original interchange  
  
1. > [!NOTE]
   >  By performing the steps in this procedure, you configure that the party that sends the interchange expects an acknowledgement back.  
  
    In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node. In the **Parties and Business Profiles** page, click the party that has the agreement for which you need to enable acknowledgement. In the **Agreement** section of the page, right-click the agreement and click **Properties**. In the **Agreement Properties** dialog box, in the one-way agreement tab (to which the inbound interchange will resolve), do the following:  
  
   1. In the **Identifiers** page, enter the values for the sender and receiver qualifiers.  
  
       For an X12-encoded acknowledgment, enter values for ISA5, ISA6, ISA7, and ISA8. For ISA5 and ISA6, enter the values for the party that will send the interchange. For ISA7 and ISA8, enter the values for the party that will receive the interchange.  
  
       For an EDIFACT-encoded acknowledgment, enter values for UNB2.1, UNB2.2, UNB3.1, and UNB3.2. For UNB2.1 and UNB2.2, enter the values for the party that will send the interchange. For UNB3.1 and UNB3.2, enter the values for the party that will receive the interchange.  
  
   2. In the **Acknowledgements** page, select properties defining the kind of acknowledgement that the sender party expects:  
  
       For X12 acknowledgements, select **TA1 Expected** and/or **997 Expected** depending on which acknowledgements are expected. For each acknowledgement type, select **Do not batch \<ACK type\>** if you want each instance of an acknowledgment to be sent as a separate interchange.  
  
       For EDIFACT acknowledgements, select **Receipt of message (CONTRL) expected** and/or **Acknowledgement (CONTRL) expected** depending on which acknowledgements are expected. For each acknowledgement type, select **Do not batch \<ACK type\>** if you want each instance of an acknowledgment to be sent as a separate interchange.  
  
   3. In the **Local Host Settings** page under the **Interchange Settings** section, clear the **Route ACK to send pipeline on request-response receive port** to return the acknowledgment asynchronously over a one-way send port. Keep this property as selected to return the acknowledgment synchronously over a two-way receive port.  
  
   4. In the **Send Ports** page, in the **Name** column of the **Send ports** grid, select the send port that you have set up to send the acknowledgment.  
  
      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses this send port setting to determine the party to use when processing the message. For more information, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
      > 
      > [!NOTE]
      >  If you have not set up the send port, you may have to perform this step later.  
  
### To configure how the party sends the acknowledgement back  
  
1. > [!NOTE]
   >  By performing the steps in this procedure, you configure how the party that received the interchange sends an acknowledgement back.  
  
    In the same **Agreement Properties** dialog box, in the other one-way agreement tab, do the following:  
  
   1. In the **Identifiers** page, enter the values for the sender and receiver qualifiers.  
  
      > [!NOTE]
      >  While sending the acknowledgement, the party that received the original interchange becomes the sender and the party that sent the original interchange becomes the receiver. Hence, the values that you enter in the Identifiers page now are opposite of the values that you entered in the one-way agreement tab in the previous step. This serves two purposes:  
      > 
      > - The acknowledgement being sent back will resolve to this one-way agreement that you are creating because the sender and receiver context properties on the acknowledgement will match the sender and receiver values you enter on the Identifiers page now.  
      >   -   Any customization you want to include in the acknowledgement can be configured on this agreement tab. For example, you can use other separators, you can choose to have CR LF enabled, etc.  
  
       For an X12-encoded acknowledgment, enter values for ISA5, ISA6, ISA7, and ISA8. For ISA5 and ISA6, enter the values for the party that will send the acknowledgement (this will be same as the party that received the original interchange). For ISA7 and ISA8, enter the values for the party that will receive the acknowledgement (this will be same as the party that sent the original interchange).  
  
       For an EDIFACT-encoded acknowledgment, enter values for UNB2.1, UNB2.2, UNB3.1, and UNB3.2. For UNB2.1 and UNB2.2, enter the values for the party that will send the acknowledgement (this will be same as the party that received the original interchange). For UNB3.1 and UNB3.2, enter the values for the party that will receive the acknowledgement (this will be same as the party that sent the original interchange).  
  
   2. For an X12 or EDIFACT acknowledgment, if required, on the **Charset and Separators** page, specify separators that you want to use in the acknowledgement. You can also specify if the acknowledgement must use a CR LF suffix.  
  
   3. For an EDIFACT acknowledgment, if required, on the **Envelopes** page under the **Interchange Settings** section, specify whether the acknowledgement would include a UNA or a UNG segment by selecting the appropriate options.  
  
## See Also  
 [Configuring EDI Acknowledgments](../core/configuring-edi-acknowledgments.md)   
 [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md)   
 [Sending an EDI Acknowledgment](../core/sending-an-edi-acknowledgment.md)   
 [How to Create a Receive Port](../core/how-to-create-a-receive-port.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)