---
title: "Agreement Resolution and Schema Determination for Outgoing EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e37aeb9d-1e95-464d-bb71-73653c1d4674
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Agreement Resolution and Schema Determination for Outgoing EDI Messages
To generate an EDI message to a trading partner, the EDI send pipeline must do the following:  
  
-   Determine the agreement that the message resolves to  
  
-   Determine the schema to use to validate the message  
  
## Agreement Resolution  
 The EDI send pipeline performs agreement lookup by performing a series of steps to determine whether there is a match between the outgoing interchange and the properties of an agreement. Once [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has determined the agreement, it determines the document schema that applies to the interchange (see below). It uses the properties associated with the matching agreement and the relevant schema to generate and validate the outgoing message.  
  
 To perform agreement resolution, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proceeds as follows:  
  
1. Resolves the agreement by matching the AgreementPartIDForSend context property with the ID of the one-way agreement. This property should be an integer type, it can be set in a custom component; it is not set by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2. If step 1 does not succeed, resolves the agreement by matching all the following three context properties with the agreement properties: AgreementNameForSend, SenderPartyNameForSend, ReceiverPartyNameForSend. Note that all the three properties must be set in order to successfully resolve to an agreement. These properties can be set in a custom component; it is not set by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3. If step 2 does not succeed, resolves the agreement by matching the party name in the message context properties with the DestinationPartyName property, which is set as additional agreement resolver in the **Identifiers** tab of agreement properties.  
  
4. If step 3 does not succeed, resolves the agreement by matching the following properties in the context of a message with those in agreement properties: DestinationPartySenderIdentifier, DestinationPartySenderQualifier, DestinationPartyReceiverIdentifier, and DestinationPartyReceiverQualifier. Note that all the four properties must be set in order to successfully resolve to an agreement. These properties can be set in a custom component; they are not set by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information, see below.  
  
   > [!NOTE]
   >  If any of the above sets of context properties are promoted and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is unable to find an agreement associated with those context properties, then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suspends the message.  
   > 
   >  If the user intentionally writes a set of context properties for agreement resolution, and if the resolver fails to identify the OnewayAgreement, then the message is suspended. On failure to resolve to an agreement based on a set of context properties, a corresponding warning message is thrown in the EventLog.  
  
5. If step 4 does not succeed or none of the above context properties are promoted, then the EDI message is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement.  
  
   > [!NOTE]
   >  If the same send port is associated with multiple agreements, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate an error.  
  
6. If no agreement is found in steps 1, 2, 3, or 4, the send pipeline uses the fallback agreement settings to generate the outgoing message.  
  
   **Agreement Resolution by Matching Sender and Receiver Context Properties**  
  
   In the second step above, the four context properties used in the match are EDI.DestinationPartySenderIdentifier, EDI.DestinationPartySenderQualifier, EDI.DestinationPartyReceiverIdentifier, and EDI.DestinationPartyReceiverQualifier. The namespace for these context properties is `http://schemas.microsoft.com/Edi/PropertySchema`. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attempts to match these values with the related sender and receiver identifiers and qualifiers in the one-way agreement properties. For X12, these fields are ISA05, ISA06, ISA07, and ISA08 in the **Identifiers** page of the one-way agreement tab in the **Agreement Properties** dialog box; for EDIFACT, these fields are UNB2.1, UNB2.2, UNB3.1, and UNB3.2 in the **Identifiers** page of the one-way agreement tab in the **Agreement Properties** dialog box.  
  
   To enable send-side agreement resolution using all four sender and receiver identifiers and qualifiers, you will have to set all four context properties. Doing so uniquely identifies the agreement. Using this method of agreement lookup gives you more flexibility in send-side processing. For example, this method may enable you to avoid creating multiple send ports in some circumstances, and to avoid complicated send port filters. It also enables you to avoid setting the OneWayAgreementId property, if desired.  
  
   If all four context properties have been set for a message, and no match is found between those context properties and the property properties, the message is suspended. The agreement will be resolved using the send port associated with an agreement only if all four context properties have not been set.  
  
> [!NOTE]
>  A message in the EDI pipeline goes to the succeeding step in Agreement Resolution till the message gets resolved with the step having Agreement in enable state. For example, if the message gets resolved in the first step of Agreement Resolution but the Agreement is in a disabled state then the message goes to the succeeding step for resolution.  
  
## Schema Determination  
 The EDI send pipeline determines the schema that applies to the message from the schema name and schema namespace contained in the intermediate XML file for each transaction set (either as doc type information or in the root node).  
  
 For an interchange that has been preserved, the send pipeline uses the doc type information in the individual transaction sets of the intermediate XML file for the complete interchange. It uses the control segment schemas for processing the envelope segments.  
  
## See Also  
 [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)