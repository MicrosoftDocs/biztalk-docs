---
title: "Known Issues with EDI Send Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1325dcd9-5dbb-48bb-b5a3-1502d1424d4e
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI Send Processing
This topic describes known issues with processing in the EDI send pipeline.  
  
## X12 Implied Decimal Point Causes Length Validation to Fail  
 **Symptom**  
  
 When the EDI send pipeline converts a base-10 numeric value in the intermediate XML to a number in the format Nn in the outgoing EDI interchange, the XML interchange fails length validation.  
  
 **Possible Cause**  
  
 When serializing an X12-encoded EDI interchange, the EDI send pipelines will always convert a base-10 numeric value to a number in the format Nn with an implied decimal point. For example, if there is a value in the intermediate XML file of 12.34, the EDI send pipeline will convert it in the EDI interchange to 1234 when it is specified as numeric type N2. The length of the base-10 numeric value will be one greater than the length of the number in the format Nn. If the length of the number in the format Nn is the maximum, the base-10 numeric value in the intermediate XML could fail XML length validation.  
  
 This is only an issue with X12-encoded interchanges.  
  
 **Resolution**  
  
 Add a value of 1 to the maximum length value of the XML number.  
  
## Control Numbers May Need to Be Reset, Archived, or Purged  
 If any control number reaches the length restriction limit for the field, BizTalk Server will raise an error and suspend the interchange. You will have to reset the control number entered in the EDI Properties or EDI Global Properties dialog box.  
  
 Control numbers are saved in the dbo.EdiSequenceNumbers table of the BizTalk MessageBox database. You should manage this database table by purging the control numbers from the table or archiving the control numbers, as appropriate.  
  
 You can also enable automatic reset of control numbers by selecting **Reset to lower limit when out of bound** in the EDI Properties dialog box.  
  
## The Data Element Name in a Context Property Name Contains an Underscore, Not a Period  
 The name of a data element within an EDI segment contains a period, for example, UNB2.1, which is the identification field for the UNB2 Sender segment. However, when the data element name is included as part of an EDI context property (for example, in the filter expression of a send port), the period is replaced with an underscore. For example, the context property for the Sender Identification data element is EDI.UNB2_1, not EDI.UNB2.1. The reason for this is that a period is not supported in a context property name.  
  
## Context Property Values from Data Elements Must Not Contain Leading or Trailing Spaces in Filter Expressions  
 If a data element in the envelope of an EDI interchange contains leading or trailing spaces, and a receive pipeline promotes a context property with the value of that data element, the receive pipeline will remove the leading or trailing spaces from the context property. As a result, if you create a filter expression with that context property, you must enter a value for the property that does not contain leading or trailing spaces. If your filter expression were to contain leading or trailing spaces, the filter expression would not resolve in a match with the context property, which will not contain leading or trailing spaces.  
  
## Default Party as Interchange Receiver Properties for Preserved Interchange Will Cause the Send Pipeline to Fail  
 If BizTalk Server receives a batched interchange that should be preserved (with the interchange suspended on error), the send pipeline that subscribes to the interchange will fail if the properties for the party as interchange receiver are set to their default values. These properties, such as ISA5, Sender qualifier, and ISA6, Sender identifier, must be set to valid values. BizTalk Server will post an error indicating that the message could not be serialized due to an invalid party configuration. This processing is not correct, because a preserved interchange has the required configuration settings, such as Sender qualifier and Sender identifier, in its headers.  
  
## The Decimal Notation in a Message Will Be Changed If the Send-Side Party or Global Setting Specifies a Different Decimal Notation  
 If the decimal notation used in an interchange is different from the decimal notation specified for outgoing messages by the UNA3 party property, BizTalk Server will change the decimal notation used in the envelope of the interchange when it serializes it for sending. This will also be the case if the UNA3 global property is used instead than the UNA3 party property. For example, if the decimal notation used in an incoming message is a period, and the UNA3 party property or the UNA3 global property that determines the decimal notation of an outgoing message specifies a comma, BizTalk Server will change the decimal notation in the outgoing message to a comma.  
  
## EDI Send Pipelines Cannot Be Executed from within an Orchestration  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can normally execute send pipelines within an Expression shape in an orchestration. However, this will not work with the EDISend pipeline or the AS2EdiSend pipeline. These pipelines must be executed within a send port. If you attempt to execute the EDISend pipeline or the AS2EdiSend pipeline in an Expression shape in an orchestration, the pipeline will not be bound to a send port, and the message will be suspended.  
  
## BizTalk EDI Application Must Not Be Modified  
 Artifacts in the BizTalk EDI Application must not be modified or deleted. If this application is modified, there is no way for you to revert to the original application by unconfiguring and reconfiguring the EDI and AS2 features.  
  
## Using the Default Row in the Functional Group Header Grid can Result in a Message-Type Mismatch Between the Interchange Header and the Group Header  
 If the value of UNH2.1 of an outgoing EDIFACT-encoded interchange does not match the value of "For message type UNH2.1" in the grid in the UNG and UNH Segment Definition page, the value of UNG1 entered in the message may not correspond to the value of UNH2.1.  
  
 This can occur because BizTalk will populate the message with the values for UNG1 in the default row of the grid even if the message does not have a match with the UNH2.1 element of that default row.  
  
 If the value of ST1 of an outgoing X12-encoded interchange does not match the value of “For ST1” in the grid in the GS and ST Segment Definition page, the value of GS1 entered in the message will be dynamically determined based on the value of ST1.  
  
## Invalid Character in Data Element  
 **Symptom**  
  
 When sending an EDI interchange using the EDI send pipeline, you may receive an error in the application event log stating that there is ‘Invalid character in data element’.  
  
 **Possible Cause**  
  
 This error can occur if a character contained in the payload data is also used as a separator. For instance, if you are using the ‘:’ character as the component separator but the payload data also contains the ‘:’ character.  
  
 This is only an issue with X12-encoded interchanges.  
  
 **Resolution**  
  
 Use the **Replace separators in payload with** setting in the **ISA Segment Definition** page of the EDI party properties to specify that separator characters found in the payload data should be replaced by the specified replacement character when sending the interchange.  
  
 For example, selecting **Replace separators in payload with** and entering the ‘&#124;’ character will replace any occurrence of a separator character in the payload data with the ‘&#124;’ character when the interchange is sent using the EDI send pipeline.  
  
## See Also  
 [Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md)   
 [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)   
 [Walkthrough (X12): Sending EDI Interchanges](../core/walkthrough-x12-sending-edi-interchanges.md)