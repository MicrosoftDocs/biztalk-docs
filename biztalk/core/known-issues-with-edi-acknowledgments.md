---
description: "Learn more about: Known Issues with EDI Acknowledgments"
title: "Known Issues with EDI Acknowledgments"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Known Issues with EDI Acknowledgments
This topic describes known issues with EDI acknowledgments in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## AK102 in a 997 Acknowledgment Can Be Negative  
 The AK102 data element (group control number) in an X12 997 acknowledgment can be a negative value. An acknowledgment with a negative AK102 data element will pass the validation performed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], even though a negative group control number is not meaningful.  
  
## A CONTRL Receipt May Report a Status of Accepted when Part of the Message Is Rejected  
 A CONTRL receipt (EDIFACT technical acknowledgment) reports a status of “Rejected” only when the incoming EDIFACT message is a duplicate or there are errors in the envelope (for example, an issue with the character set). EDIFACT does not report a state of “Interchange accepted with errors” in the CONTRL technical acknowledgment, as X12 does in the TA104 field in a TA1 acknowledgment. If part of the EDIFACT message is accepted, the CONTRL technical acknowledgment will report “Accepted”. In some scenarios, part of the message will be rejected, but the CONTRL acknowledgment will still report a status of “Accepted”. In such scenarios, the UCI5 element may report the error.  
  
## X12 Acknowledgments Will Show Accepted for a Preserved Interchange (Suspend Interchange on Error) When a Group Header or Trailer is in Error  
 If the inbound batch processing option for an X12 message is set to “Preserve Interchange – suspend interchange on error”, and a field in the group header or trailer is invalid, the status will be reported as Accepted in both TA1 and 997 acknowledgments. The EDI status report and transaction set details will also indicate a status of Accepted. This occurs even though the interchange will be suspended, and an error in the Event Viewer will indicate that the interchange was suspended.  
  
 The TA1 acknowledgment will show a status of Accepted because it is intended to verify the correctness of the ISA header and IEA trailer, but not the correctness of the GS header and GE trailer. However, the 997 acknowledgment will also show a status of Accepted.  
  
## If groups in an interchange have the same name, the status report will show twice as many acknowledgments  
 If BizTalk Server processes an EDI interchange with multiple groups that have the same name, the EDI Interchange and Correlated ACK status report will list twice as many functional acknowledgments as expected. For example, if two groups in an interchange have the same name, the status report will list four acknowledgments, rather than two.  
  
## See Also  
 [Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md)   
 [Sending an EDI Acknowledgment](../core/sending-an-edi-acknowledgment.md)   
 [Processing a Received Acknowledgment](../core/processing-a-received-acknowledgment.md)   
 [Configuring EDI Acknowledgments](../core/configuring-edi-acknowledgments.md)
