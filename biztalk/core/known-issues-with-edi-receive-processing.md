---
title: "Known Issues with EDI Receive Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbb3fd6a-381b-479e-a9f2-7b6371fac39e
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI Receive Processing
This topic describes known issues with processing in the EDI receive pipeline.  
  
## Receive-Side Processing of Trailing Separators Fails  
 **Symptom**  
  
 A transaction set with a trailing separator fails with error code AK403= 6 for an X12-encoded message or error codes UCM3=4/UCD1=45 for an EDIFACT-encoded message.  
  
 **Possible Cause**  
  
 Processing of trailing separators is not enabled.  
  
 **Resolution**  
  
 Open the EDI Properties for the party that sent the message. In the Validation and ACK Generation page of the EDI Properties dialog box (for either X12 or EDIFACT), select "Allow trailing delimiter/separators". After clicking this checkbox, you can specify that empty XML tags are created for trailing separators in the intermediate XML by clicking "Create empty XML tags for trailing separators".  
  
## CONTRL ACK is enabled, but not generated  
 **Symptom**  
  
 The Generate Functional ACK checkbox in the Validation and ACK Generation for the sending party is checked, but the EDI receive pipeline has not generated a CONTRL acknowledgment.  
  
 **Possible Cause**  
  
 The CONTRL message contains several mandatory data elements that must be copied from the interchange. If the data element in the interchange is missing or is syntactically invalid, the receive pipeline cannot generate a syntactically valid CONTRL message.  
  
 **Resolution**  
  
 Report the error condition by some other means than a CONTRL acknowledgment.  
  
## "There Was a Failure Executing the Receive Pipeline…" Error Message  
 **Symptom**  
  
 Attempting to run an AS2 receive pipeline results in an 80040154 error.  
  
 **Possible Cause**  
  
 Pipelines are not supported on 64-bit host instances.  
  
 **Resolution**  
  
 Associate the pipeline with a 32-bit host.  
  
## An X12-Encoded Message Is Suspended If Port-Based Authentication Is Enabled and BizTalk Server Does Not Have Access to the Authorization and Security Information  
 **Symptom**  
  
 When a message is received over a receive port for which authentication is enabled, and the party that sent the message cannot be determined, BizTalk Server will suspend the message.  
  
 **Possible Cause**  
  
 If authentication is enabled for a receive port (the "No Authentication" property for the receive port is cleared), BizTalk Server requires settings for the "ISA1-2 (Authorization qualifier and information)" and "ISA3-4 (Security qualifier and information)" properties in order to process the interchange. These properties are set for a party in the X12 Interchange Processing Properties page for the party as an interchange sender. If BizTalk Server cannot determine the values of these properties, it will suspend the message.  
  
 This can occur in two ways. In the first case, if BizTalk Server cannot determine the party that sent the message, it will use the EDI global properties and will not have access to the authorization and security settings. As a result, it will suspend the message. In the second case, if BizTalk Server determines the party, but the ISA1-2 and ISA3-4 properties for the party are not configured, BizTalk Server will again not have access to authorization and security information and will suspend the message.  
  
 **Resolution**  
  
 Make sure that the sending party for the message can be identified and that the ISA1-2 and ISA3-4 properties are defined in the party agreement.  
  
## Incorrect SE01 in a split HIPAA subdocument  
 **Symptom**  
  
 The transaction set trailer (SE01 field) provides a count of the data segments, including the header and trailer segments of an X12/HIPAA document. However, for a split HIPAA sub document, the EDI receive pipeline applies the same SE01 value as the original document, instead of re-computing it.  
  
 **Cause**  
  
 The EDI receive pipeline copies the value of SE01 from the original HIPAA document to a split sub document.  
  
## Error Message for Duplicate UNB5 or UNH1 Is Not Descriptive  
 If BizTalk Server receives a message that has a duplicate UNB5 (interchange control number) or UNH1 (transaction set reference number), the error code and description that it posts will not clearly indicate the nature of the problem.  
  
## BizTalk Server Will Suspend a Very Large Interchange If It Runs Out of Memory  
 BizTalk Server may run out of memory when it parses a very large interchange. If it does, it will post an error and suspend the interchange. In the Group Hub page, you will not be able to see all of the contents of a very large interchange that has been suspended. You will be able to see the initial part of the message, but BizTalk Server is limited in the amount of data from a suspended interchange that it can display.  
  
## Korean Characters Added to an Enumeration in a KEDIFACT Schema Must Be in UNICODE  
 When BizTalk Server receives a KEDIFACT-encoded interchange with Korean characters, it will use the code page/character set value in the UNB2 field to process the interchange. However, if you modify a KEDIFACT schema by adding a Korean character with an ID data type to an enumeration, you must add the value in UTF-16 UNICODE, as specified at the top of the schema.  
  
## Executing an EDI Receive Pipeline from within an Orchestration Is Not Supported  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can typically execute receive pipelines within an Expression shape in an orchestration. This functionality has not been tested for the EDIReceive pipeline or the AS2EdiReceive pipeline, so is not supported.  
  
## BizTalk EDI Application Must Not Be Modified  
 Artifacts in the BizTalk EDI Application must not be modified or deleted. If this application is modified, there is no way for you to revert to the original application by unconfiguring and reconfiguring the EDI and AS2 features.  
  
## See Also  
 [Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md)   
 [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)   
 [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)