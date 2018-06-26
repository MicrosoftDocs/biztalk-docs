---
title: "Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 503e307c-4cb0-49b5-8751-82dcea203151
caps.latest.revision: 45
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages
When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message, the EDI receive pipeline performs trading partner agreement lookup, schema discovery, and authorization processes to determine how to process the message.  
  
## Agreement Resolution  
 The EDI receive pipeline performs a trading partner agreement resolution by performing a series of steps to determine whether there is a match between header fields in the message and properties in the agreement definition. Once [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has determined the agreement, it determines the document schema that applies to the interchange (see below). It uses the properties associated with the matching agreement and the relevant schema to validate and process the received message.  
  
 To perform agreement resolution, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proceeds as follows:  
  
1. Resolve the agreement by matching the sender qualifier and identifier, and the receiver qualifier and identifier, in the interchange header with those in the properties of an agreement.  
  
2. If step 1 does not succeed, resolve the agreement by matching just the sender qualifier and identifier in the interchange header with those in the properties of an agreement. Also, because the first step did not succeed, it is safe to assume that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will be receiving the message. Hence, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tries to match the receiver qualifier and identifier with the following:  
  
   -   Values “BT” and “HostX12Recvr” (for X12-encoded messages) and  
  
   -   Values “BT” and “HostEdifactRecvr” (for EDIFACT-encoded messages)  
  
   > [!IMPORTANT]
   > - **BizTalk Server 2013 R2, 2013, and 2010**: The ISA5, ISA6, ISA7, ISA8, UNB2.1, UNB2.2, UNB3.1, and UNB3.2 fields are mandatory in the agreement settings.  
   >   -   **BizTalk Server 2009 and 2006 R2**: The ISA7, ISA8, UNB3.1, and UNB3.2 fields are not mandatory in the party settings. If the fields are left blank, the EDI engine gives a resolution based on the values of ISA5, ISA6, UNB2.1, and UNB2.2.  
   >   -   To support the resolutions from BizTalk Server 2009 and 2006 R2 to newer versions of BizTalk Server, the hard coded IDs (HostX12Recvr and HostEdifactRecvr) and qualifiers (BT) are introduced.  
   >   -   Your EDIFACT messages should follow the [UNECE guidelines](http://www.unece.org/tradewelcome/areas-of-work/un-centre-for-trade-facilitation-and-e-business-uncefact/outputs/standards/unedifact/tradeedifactrules.html) for message syntax and rules.  
  
3. If step 2 does not succeed, use the fallback agreement properties.  
  
   In the first step, for X12, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use the following values to make the match:  
  
- ISA05 (sender qualifier)  
  
- ISA06 (sender identifier)  
  
- ISA07 (receiver qualifier)  
  
- ISA08 (receiver identifier)  
  
  For EDIFACT, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use the following values to make the match:  
  
- UNB2.1 (sender identifier)  
  
- UNB2.2 (sender qualifier)  
  
- UNB3.1 (receiver identifier)  
  
- UNB3.2 (receiver qualifier)  
  
  The agreement properties used for the match are defined in the **Identifiers** page of the direction-specific agreement tabs of the **Agreement Properties** dialog box.  
  
  These four receive-side and send-side properties uniquely identify the trading partner agreement. Using the four properties gives you more flexibility in receive-side processing. For example, this method of agreement resolution may enable you to send acknowledgments to multiple parties without creating multiple send ports.  
  
  If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement using all four sender and receiver qualifiers and identifiers, it will attempt to resolve the agreement using just the sender qualifier and identifier. For X12, these fields are ISA05 and ISA06; for EDIFACT, these fields are UNB2.1 and UNB2.2. As with a match of sender and receiver properties, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] matches the values in the interchange header with the agreement properties defined in the **Identifiers** page of the direction-specific agreement tabs of the **Agreement Properties** dialog box. If only the sender qualifier and identifier are used to resolve the agreement, the receiver qualifier and identifier should be undefined in the bi-directional agreement tab of the **Agreement Properties** dialog box.  
  
  If no agreement is found, then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback trading partner agreement, unless the port setting requires authentication. If the port setting requires authentication (if either **Drop messages if authentication fails** or **Keep messages if authentication fails** is selected on the **General** page of the **Receive Port Properties**), an agreement is required for any interchange received by the receive port. In this case, if the agreement is not resolved by matching the interchange header with agreement properties, using the fallback agreement properties to determine the agreement is not allowed. The interchange will be treated as though authentication had failed if no agreement is found, and will be suspended.  
  
> [!NOTE]
>  A message in the EDI pipeline goes to the succeeding step in Agreement Resolution till the message gets resolved with the step having Agreement in enable state. For example, if the message gets resolved in the first step of Agreement Resolution but the Agreement is in a disabled state then the message goes to the succeeding step for resolution.  
  
## Schema Discovery  
 After [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has determined the agreement that resolves to the message, it must determine the schema that it should use to validate and process the message. It does so using the properties identified in the **Local Host Settings** page of the one-way (send side) agreement tab of the **Agreement Properties** dialog box.  
  
 To determine the schema, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must first determine the schema namespace. The EDI Disassembler will either use a default namespace for the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], or it will determine the namespace to be used for a custom schema.  
  
 The **Local Host Settings** page of the one-way agreement tab of the **Agreement Properties** dialog box enables you to set up a grid of values to determine a custom namespace. If no match is found in that grid, the EDI Disassembler uses the default namespace in the **Target namespace** field marked for the default row.  
  
### X12 Schema Discovery  
 For X12-encoded messages, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines a custom namespace using the application sender identifier (GS02) and the transaction set ID (ST01) from the header of the incoming interchange. It attempts to find a match between these values and the values for the GS02 and ST01 properties in the **Customize target namespace** grid in the **Local Host Settings** page (under **Transaction Set Settings**) of the bi-directional agreement tab of the **Agreement Properties** dialog box. If it finds a match, it will use the target namespace identified in the same row of the grid to determine which schema to us to validate and process the message. If the target namespace is not determined, then the default target namespace will be used. If no namespace is identified in the **Target namespace** field marked for the default row, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use the target namespace identified in the fallback agreement properties for X12-encoded messages, which by default is `http://schemas.microsoft.com/BizTalk/Edi/X12/2006`.  
  
 For X12 interchanges, after the target namespace is discovered, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema using the following information:  
  
- The target namespace just discovered  
  
- The version/release in the first five characters of ST03 (if GS07 == X - Accredited Standards Committee X12). If ST03 is not present/invalid or does not result in the schema resolution, then the version is determined by the first five characters of GS08 or of ISA12 (if GS07 != X).  
  
- The DocType in ST01.  
  
  The EDI Disassembler concatenates the encoding type, version/release, and DocType to determine the schema name, for example, "X12_00401_864". It then concatenates the target namespace with the schema name, for example, `http://schemas.microsoft.com/BizTalk/Edi/X12/2006/X12#X12_00401_864`.  
  
  For an incoming HIPAA 837 interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports three HIPAA 837 schemas:  
  
|837 Schema|GS08 Value in version 4010|GS08/ST03 Value in version 5010|  
|----------------|--------------------------------|--------------------------------------|  
|Claim-Dental_837D|004010X097A1|005010X224A1|  
|Claim-Institutional_837I|004010X096A1|005010X223A1|  
|Claim-Professional_837P|004010X098A1|005010X222|  
  
> [!NOTE]
>  In HIPAA versions, for the transaction set 278 (Health Care Services Review), both the request and response pairs share the same value for GS08 and ST01. Depending on the trigger values in BHT02 field you may differentiate between a 278 Request/ Response in version 5010:  
> 
> 1. Any of the values 01, 13 and 36 in BHT02 indicates a Health Care Services Review Request  
>    2.  11 in BHT02 indicates Health Care Services Review Response  
  
### EDIFACT Schema Discovery  
 For EDIFACT-encoded messages, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines a custom namespace using the message type (UNH2.1), message version number (UNH2.2), message release number (UNH2.3), assigned code (UNH2.5), functional group ID (UNG2.1), and application send code qualifier (UNG2.2) from the header of the incoming interchange. It then attempts to find a match between these values and the values for the UNH2.1, UNH2.2, UNH2.3, UNH2.5, UNG2.1, and UNG2.2 properties in the **Customize target namespace** grid (under **Transaction Set Settings**) of the bi-directional agreement tab of the **Agreement Properties** dialog box. If it finds a match, it will use the target namespace identified in the same row of the grid to determine which schema to use to validate and process the message. If the target namespace is not determined, then the default target namespace will be used. If no namespace is identified in the **Target namespace** field marked for the default row, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use the target namespace identified in the fallback agreement properties for EDIFACT-encoded messages, which by default is `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006`.  
  
 For EDIFACT interchanges, once the target namespace is discovered, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema using the following information:  
  
- The target namespace just discovered.  
  
- The message version number in UNH2.2.  
  
- The message release number in UNH2.3.  
  
- The message type in UNH2.1.  
  
- The assigned code in UNH2.5.  
  
  The EDI Disassembler concatenates the encoding type, the version, the release, and the message type to determine the schema name, for example, " EFACT_D94A_CONTEN". It then concatenates the target namespace with the schema name, for example, `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006/EFACT#EFACT_D94A_CONTEN`.  
  
  If UNH2.5 is present in the message, the EDI Disassembler will first attempt to find a matching schema by using the value of UNH2.5 as part of the schema name, for example “EFACT_D94A_CONTEN_TEST”. If no matching schema is found, the EDI Disassembler will fall back to finding the schema without the UNH2.5 value.  
  
## Authorization  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] checks the values of the authorization and security fields defined for the agreement with the fields in the message. If there is a mismatch, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange. For EDIFACT-encoded messages, these fields are the recipient reference password (UNB6.1 and UNB6.2). For X12-encoded messages, these fields are the Authorization qualifier and information (ISA1-2) and Security qualifier and information (ISA3-4).  
  
## See Also  
 [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)