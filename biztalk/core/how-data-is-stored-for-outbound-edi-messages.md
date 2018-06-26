---
title: "How Data Is Stored for Outbound EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6e576fc-37fd-417d-ae68-607a0a8bcc0a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How Data Is Stored for Outbound EDI Messages
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does the following to generate a status report entry for an outbound interchange:  
  
1.  When outbound message XML is sent to the EDI send pipeline, the send pipeline creates an entry in the status reporting data store with the following values:  
  
    -   Interchange status entry is set to Processed  
  
    -   Interchange ACK status entry (one per interchange) is set to Expected  
  
    -   Functional ACK status entries (one per group in X12, one for all groups in EDIFACT) are set to Expected  
  
2.  After the EDI message has been sent to the trading partner, and the acknowledgment has been returned from the trading partner, the EDI receive pipeline that receives the acknowledgment updates the Interchange status, the Interchange ACK status, and the Functional ACK status entries to Accepted/Partially Accepted/Rejected, as appropriate.  
  
## Data Stored by the Send Pipeline for Outbound Interchanges  
 The send pipeline creates a record in the status report data store for each interchange that it sends. Most data required for the entry is available from the interchange header/trailer segments (ISA/IEA or UNB/UNZ). Other data is available from send port properties. The data stored includes:  
  
-   Record Type = Interchange Status  
  
-   Interchange Direction = Update Data = Send  
  
-   Interchange Receiver = Update Data  
  
-   Interchange Sender = Update Data  
  
-   Interchange Date = Update Data  
  
-   Interchange Time = Update Data  
  
-   Interchange Control ID = Update Data  
  
-   Interchange Status: Processed/Sent. A status of Processed indicates that the send pipeline has successfully processed the interchange and handed it over to the send adapter for delivery.  
  
-   Interchange Control Count (Groups/Messages in X12 respectively) = Data  
  
-   Interchange Send Port ID = Data  
  
## Data Stored by the Receive Pipeline for Each Technical Acknowledgment Received in Response to an Outbound Interchange  
 The receive pipeline creates a record in the status report data store for each technical acknowledgment that it receives. The receive pipeline creates a record of each interchange received in the status report data store. creates one technical acknowledgment status report entry in the data store for each technical ACK received as a response to an interchange sent to a trading partner. The technical acknowledge is the TA1 for X12 and the CONTRL message with only the UCI Segment for EDIFACT. The data stored includes:  
  
- Record Type = Interchange ACK Status  
  
- Interchange ACK Direction = Send – Update Data  
  
- Interchange Receiver = Update Data (required for correlation)  
  
- Interchange Sender = Update Data (required for correlation)  
  
- Interchange Date = Update Data (required for X12 correlation)  
  
- Interchange Control ID = Update Data (required for correlation)  
  
- Interchange ACK Status = Generated or Not Applicable \<Refer Note 0\> - Update Data  
  
- Interchange ACK Control ID= Not valued – will be applied by send side  
  
- Interchange ACK Date = Not valued – will be applied by send side  
  
- Interchange ACK Time = Not valued – will be applied by send side  
  
- ACK/Action Code = Update Data  \<refer note 1\> (from X12-TA104 or EDIFACT-UCI4)*  
  
- ACK Note Code = Update Data \<Refer Note 2\> (from X12-TA105, not applicable for EDIFACT)*  
  
  The following ACK/Action Codes are used:  
  
|Data in ACK/Action Code|Error description for Reporting|Comment (applicability)|  
|------------------------------|-------------------------------------|-------------------------------|  
|A|Accepted|X12|  
|E|Accepted, errors noted|X12|  
|P|Partially Accepted|X12|  
|R|Rejected|X12|  
|4|Rejected|EDIFACT|  
|8|Accepted/Partially Accepted|EDIFACT|  
  
 The following ACK Note Codes are used:  
  
|Data in ACK Note Code (in X12)|Description|  
|--------------------------------------|-----------------|  
|000|Success|  
|001|Interchange Control Number mismatch|  
|002|Standard not supported|  
|003|Version of the Controls Not Supported|  
|004|Segment Terminator is Invalid|  
|005|Invalid Interchange ID Qualifier for Sender|  
|006|Invalid Interchange Sender ID|  
|007|Invalid Interchange ID Qualifier for Receiver|  
|008|Invalid Interchange Receiver ID|  
|009|Unknown Interchange Receiver ID|  
|010|Invalid Authorization Information Qualifier Value|  
|011|Invalid Authorization Information Value|  
|012|Invalid Security Information Qualifier Value|  
|013|Invalid Security Information Value|  
|014|Invalid Interchange Date Value|  
|015|Invalid Interchange Time Value|  
|016|Invalid Interchange Standards Identifier Value|  
|017|Invalid Interchange Version ID Value|  
|018|Invalid Interchange Control Number Value|  
|019|Invalid Acknowledgment Requested Value|  
|020|Invalid Test Indicator Value|  
|021|Invalid Number of Included Groups Value|  
|022|Invalid Control Structure|  
|023|Improper End-of-File|  
|024|Invalid Interchange Content|  
|025|Duplicate Interchange Control Number|  
|026|Invalid Data Element Separator|  
|027|Invalid Component Element Separator|  
|028|Invalid Delivery Date in Deferred Delivery Request|  
|029|Invalid Delivery Time in Deferred Delivery Request|  
|030|Invalid Delivery Time Code in Deferred Delivery  Request|  
|031|Invalid Grade of Service|  
  
## Data Updated by the Receive Pipeline for Each Technical Acknowledgment Received in Response to an Outbound Interchange  
 For each technical acknowledgment that the receive pipeline receives, it updates the status report entry for the correlated sent interchange.  
  
 The EDI Disassembler locates records in the data store using data in the UCI and TA1 Segments of the incoming acknowledgment, as follows:  
  
|Fields in ACK|Fields in Data store|Comment|  
|-------------------|--------------------------|-------------|  
|Interchange Sender ID|Interchange Receiver|-|  
|Interchange Receiver ID|Interchange Sender|-|  
|-|Interchange Date|-|  
|Interchange Control Number|Interchange Control ID|-|  
|-|Interchange Direction = Send|Required in preserved batch scenario for uniqueness|  
|Record Type|Interchange Status and Interchange ACK Status|-|  
  
 The data stored includes:  
  
- Interchange ACK Direction = Receive – Existing Data  
  
- Interchange ACK Status = Received  
  
- Interchange Receiver = Existing Data  
  
- Interchange Sender = Existing Data  
  
- Interchange Date = Existing Data  
  
- Interchange Control ID = Existing Data  
  
- Interchange ACK Control ID= Update Data  
  
- Interchange ACK Date = Update Data  
  
- Interchange ACK Time = Update Data  
  
- ACK/Action Code = Update Data (from X12-TA104 or EDIFACT-UCI4)* \<Refer Note 1\>  
  
- ACK Note Code 2 = Update Data (from X12-TA105 and not valued for EDIFACT)* \<Refer Note 2\>  
  
  The data from the ACK X12:TA1-104 or EDIFACT UCI4 is to be mapped as follows:  
  
|Data in ACK/Action Code|Mapped for Status Reporting|Comment|  
|------------------------------|---------------------------------|-------------|  
|A|Accepted|X12|  
|P|Partially Accepted|X12|  
|R, M, W, X|Rejected|X12|  
|E|Accepted with errors|X12|  
|4|Rejected|EDIFACT|  
|7, 8|Accepted/Partially Accepted|EDIFACT|  
  
 The following ACK Note Codes are used:  
  
|Data in ACK Note Code (in X12)|Mapped for Status Reporting|  
|--------------------------------------|---------------------------------|  
|000|Success|  
|001|Interchange Control Number mismatch|  
|002|Standard not supported|  
|003|Version of the Controls Not Supported|  
|004|Segment Terminator is Invalid|  
|005|Invalid Interchange ID Qualifier for Sender|  
|006|Invalid Interchange Sender ID|  
|007|Invalid Interchange ID Qualifier for Receiver|  
|008|Invalid Interchange Receiver ID|  
|009|Unknown Interchange Receiver ID|  
|010|Invalid Authorization Information Qualifier Value|  
|011|Invalid Authorization Information Value|  
|012|Invalid Security Information Qualifier Value|  
|013|Invalid Security Information Value|  
|014|Invalid Interchange Date Value|  
|015|Invalid Interchange Time Value|  
|016|Invalid Interchange Standards Identifier Value|  
|017|Invalid Interchange Version ID Value|  
|018|Invalid Interchange Control Number Value|  
|019|Invalid Acknowledgment Requested Value|  
|020|Invalid Test Indicator Value|  
|021|Invalid Number of Included Groups Value|  
|022|Invalid Control Structure|  
|023|Improper End-of-File|  
|024|Invalid Interchange Content|  
|025|Duplicate Interchange Control Number|  
|026|Invalid Data Element Separator|  
|027|Invalid Component Element Separator|  
|028|Invalid Delivery Date in Deferred Delivery Request|  
|029|Invalid Delivery Time in Deferred Delivery Request|  
|030|Invalid Delivery Time Code in Deferred Delivery  Request|  
|031|Invalid Grade of Service|  
  
## Data Stored by the Receive Pipeline for Each Functional Acknowledgment Received in Response to Outbound Interchanges  
 The receive pipeline creates a record in the status report data store for each functional acknowledgment that it receives.  The technical acknowledge is the 997 for X12 and the full CONTRL message for EDIFACT. One entry per group will to be created. Data from the interchange and group headers is used while making this entry. The data stored includes:  
  
- Record Type = Functional ACK Status  
  
- Functional ACK Direction = Send  
  
- Functional ACK Status = \<Generated or Not Applicable, refer note 1\>  
  
- Interchange Receiver = Update Data (required for correlation)  
  
- Interchange Sender = Update Data (required for correlation)  
  
- Interchange Date = Update Data (required for X12 correlation)  
  
- Interchange Control ID = Update Data (required for correlation)  
  
- Group Control Number = Update Data (‘optional for EDIFACT’ and required for X12 correlation)  
  
- Functional ID Code = Update Data (GS01/UNG01)  
  
- Count of Transaction Sets = Update Data (UNE1/UNZ1)  
  
- Functional ACK Interchange Control ID= Not value – will be applied by send side  
  
- Functional ACK Interchange Date = Not valued – will be applied by send side  
  
- Functional ACK Interchange Time = Not valued – will be applied by send side  
  
- Count of Transaction Sets Received = Update Data (X12-AK903 and computed by Engine for EDIFACT encoding)  
  
- Count of Transaction Sets Accepted = Update Data (X12-AK904 and computed by Engine for EDIFACT engine)  
  
- ACK/Action Code = Update Data  \<refer note 2\> (from X12-AK901 or EDIFACT-UCI4)*  
  
- Error/Syntax Error Code  = Update Data (X12-AK905, EDIFACT UCI5) Note 3  
  
- Additional X12 ACK Error Code 2 = Update Data (X12-AK906)  
  
- Additional X12 ACK Error Code 3 = Update Data (X12-AK907)  
  
- Additional X12 ACK Error Code 4 = Update Data (X12-AK908)  
  
- Additional X12 ACK Error Code 5 = Update Data (X12-AK909)  
  
  The following ACK/Action Codes will be used:  
  
|Data in ACK/Action Code|Error description for Reporting|Comment (applicability)|  
|------------------------------|-------------------------------------|-------------------------------|  
|A|Accepted|X12|  
|E|Accepted  with errors|X12|  
|P|Partially Accepted|X12|  
|R|Rejected|X12|  
|4|Rejected|EDIFACT|  
|7|Accepted/Partially Accepted|EDIFACT|  
  
 The following Error/Syntax Error Codes will be used for EDIFACT:  
  
|Data in Error/Syntax Error Code<br /><br /> (applicable to EDIFACT)|Error Description for reporting|  
|--------------------------------------------------------------------|-------------------------------------|  
|2|Syntax version or level not supported|  
|7|Interchange recipient not actual recipient|  
|12|Invalid value|  
|13|Missing|  
|14|Value not supported in this position|  
|15|Not supported in this position|  
|16|Too many constituents|  
|17|No agreement|  
|18|Unspecified error|  
|19|Invalid decimal notation|  
|20|Character invalid as service character|  
|21|Invalid character(s)|  
|22|Invalid service character(s)|  
|23|Unknown Interchange sender|  
|24|Too old|  
|25|Test indicator not supported|  
|26|Duplicate detected|  
|27|Security function not supported|  
|28|References do not match|  
|29|Control count does not match number of instances received|  
|30|Groups and messages/packages mixed|  
|31|More than one message type in group|  
|32|Lower level empty|  
|33|Invalid occurrence outside message, package, or group|  
|34|Nesting indicator not allowed|  
|35|Too many data element or segment repetitions|  
|36|Too many segment group repetitions|  
|37|Invalid type of character(s)|  
|38|Missing digit in front of decimal sign|  
|39|Data element too long|  
|40|Data element too short|  
|41|Permanent communication network error|  
|42|Temporary communication network error|  
|43|Unknown interchange recipient|  
|45|Trailing separator|  
|46|Character set not supported|  
|47|Envelope functionality not supported|  
|48|Dependency condition violated|  
|70|Transaction set is missing or invalid transaction set Identifier|  
|71|Transaction set or group control number mismatch|  
|72|Unrecognized segment ID|  
|73|XML not at correct position|  
|74|Too few segment group repetitions|  
|75|Too few segment repetitions|  
|76|Too few data elements found|  
  
 The following Error/Syntax Error Codes will be used for X12:  
  
|Data in Error/Syntax Error Code<br /><br /> (applicable to X12)|Error Description for reporting|  
|----------------------------------------------------------------|-------------------------------------|  
|1|Functional group not supported|  
|2|Functional group version not supported|  
|3|Functional group trailer missing|  
|4|Group control number in the functional group header and trailer do not agree|  
|5|Number of included transaction sets does not match actual count|  
|6-26|Other unsupported validation errors|  
  
## Data Updated by the Receive Pipeline for Each Functional Acknowledgment Received in Response to Outgoing Interchanges  
 For each functional acknowledgment that the receive pipeline receives, it updates the status report entry for the correlated sent interchange.  
  
 The EDI Disassembler locates records in the data store using data in the Interchange and Group Header Segments of the incoming acknowledgment, as follows:  
  
|Fields in ACK|Fields in Data store|Comment|  
|-------------------|--------------------------|-------------|  
|Interchange Sender ID|Interchange Receiver|Applicable to both X12 and EDIFACT|  
|Interchange Receiver ID|Interchange Sender|Applicable to both X12 and EDIFACT|  
|-|Interchange Date|-|  
|Interchange Control Number|Interchange Control ID|Applicable only to EDIFACT|  
|Group Control Number|Group Control Number|Applicable only to X12|  
|-|Interchange Direction = Send|Required since in BIBO Scenario for uniqueness|  
|Record Type|Functional ACK Status|Applicable to both X12 and EDIFACT|  
  
 The data stored includes:  
  
- Record Type = Functional ACK Status  
  
- Functional ACK Direction = Receive  
  
- Functional ACK Status =Update Data as Received  
  
- Interchange Receiver = Existing Data  
  
- Interchange Sender = Existing Data  
  
- Interchange Date = Existing Data  
  
- Interchange Control ID = Existing Data  
  
- Group Control Number = Existing Data  
  
- Functional ID Code = Existing Data  
  
- Count of Transaction Sets = Existing Data  
  
- Functional ACK Interchange Control ID= Update Data  
  
- Functional ACK Interchange Date = Update Data  
  
- Functional ACK Interchange Time = Update Data  
  
- Count of Transaction Sets Delivered = Update Data (X12 AK903 and not applicable for EDIFACT)  
  
- Count of Transaction Sets Accepted = Update Data (X12 AK904 and not applicable for EDIFACT)  
  
- ACK/Action Code = Update Data (X12 AK901 and UCI4) Refer Note 1  
  
- Error/Syntax Error Code  = (X12 AK905 and UCI5) Refer Note 2  
  
- Additional X12 ACK Error Code 2 = Update Data (X12-AK906)  
  
- Additional X12 ACK Error Code 3 = Update Data (X12-AK907)  
  
- Additional X12 ACK Error Code 4 = Update Data (X12-AK908)  
  
- Additional X12 ACK Error Code 5 = Update Data (X12-AK909)  
  
  The following ACK/Action Codes will be used:  
  
|Data in ACK/Action Code|Mapped for Status Reporting|Comment|  
|------------------------------|---------------------------------|-------------|  
|A|Accepted|X12|  
|P|Partially Accepted|X12|  
|R, M, W, X|Rejected|X12|  
|E|Accepted with errors|X12|  
|4|Rejected|EDIFACT|  
|7, 8|Accepted/Partially Accepted|EDIFACT|  
  
 The following Error/Syntax Error Codes will be used for EDIFACT:  
  
|Data in Error/Syntax Error Cod<br /><br /> (applicable to EDIFACT)|Error Description for reporting|  
|-------------------------------------------------------------------|-------------------------------------|  
|2|Syntax version or level not supported|  
|7|Interchange recipient not actual recipient|  
|12|Invalid value|  
|13|Missing|  
|14|Value not supported in this position|  
|15|Not supported in this position|  
|16|Too many constituents|  
|17|No agreement|  
|18|Unspecified error|  
|19|Invalid decimal notation|  
|20|Character invalid as service character|  
|21|Invalid character(s)|  
|22|Invalid service character(s)|  
|23|Unknown Interchange sender|  
|24|Too old|  
|25|Test indicator not supported|  
|26|Duplicate detected|  
|27|Security function not supported|  
|28|References do not match|  
|29|Control count does not match number of instances received|  
|30|Groups and messages/packages mixed|  
|31|More than one message type in group|  
|32|Lower level empty|  
|33|Invalid occurrence outside message, package, or group|  
|34|Nesting indicator not allowed|  
|35|Too many data element or segment repetitions|  
|36|Too many segment group repetitions|  
|37|Invalid type of character(s)|  
|38|Missing digit in front of decimal sign|  
|39|Data element too long|  
|40|Data element too short|  
|41|Permanent communication network error|  
|42|Temporary communication network error|  
|43|Unknown interchange recipient|  
|45|Trailing separator|  
|46|Character set not supported|  
|47|Envelope functionality not supported|  
|48|Dependency condition violated|  
|70|Transaction set is missing or invalid transaction set Identifier|  
|71|Transaction set or group control number mismatch|  
|72|Unrecognized segment ID|  
|73|XML not at correct position|  
|74|Too few segment group repetitions|  
|75|Too few segment repetitions|  
|76|Too few data elements found|  
  
 The following Error/Syntax Error Codes will be used for X12:  
  
|Data in Error/Syntax Error Code<br /><br /> (applicable to X12)|Error Description for reporting|  
|----------------------------------------------------------------|-------------------------------------|  
|1|Functional group not supported|  
|2|Functional group version not supported|  
|3|Functional group trailer missing|  
|4|Group control number in the functional group header and trailer do not agree|  
|5|Number of included transaction sets does not match actual count|  
|6-26|Other unsupported validation errors|  
  
## See Also  
 [How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [How Data Is Stored for Inbound EDI Messages](../core/how-data-is-stored-for-inbound-edi-messages.md)