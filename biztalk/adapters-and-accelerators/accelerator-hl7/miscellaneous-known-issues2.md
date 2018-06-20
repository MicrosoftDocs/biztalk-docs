---
title: "Miscellaneous Known Issues2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "known issues"
ms.assetid: 01cd896f-6c7f-4734-b953-81a92195a5c0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Miscellaneous Known Issues
This section contains useful information about miscellaneous errors.  
  
## Duplicate errors logged for the same message segment, sequence, and field number  
 If there are errors in components of a field of complex data types, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will report one error for each such error. The segment ID and field number will be identical. The error number and description may be different because the HL7 error reporting mechanism does not support reporting errors at the component and subcomponent level.  
  
## Segment sequence errors  
 If required message segments are missing, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reports a "Segment sequence error (Unexpected end of message body found)" message in the last correct segment parsed by the engine.  
  
## Invalid error can be recorded when the MSH3 header field is structurally incorrect  
 If an MSH3 header field is structurally incorrect, the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer cannot copy the MSH3 field contents into the MSH5 header, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] cannot send an acknowledgment (ACK). This may indicate that the problem was with the MSH5 field, not the MSH3 field.  
  
## Access Database Errors  
 The HL7 Access databases contained the following errors:  
  
- Field 27 of the OBR segment in the HL7 V2.3 Access database was incorrectly marked as non-repeatable and required. A change has occurred in this [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] schemas field to the correct values of repeatable and optional.  
  
- Field 2 of the OBX segment in the HL7 V2.3 Access database was incorrectly marked as required, and field 10 of the OBX segment in the HL7 V2.3 Access database was incorrectly marked as non-repeatable. In the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] schemas, field 2 is marked as optional and field 10 is marked as repeatable.  
  
- Field 4 of the OBX segment in the HL7 V2.3.1 Access database was incorrectly marked as required. This field in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] schemas is marked correctly as optional.  
  
## Logging service account may not have access to databases that are not created by the setup program  
 When you configure the Logging store to point to a newly created database, which the setup program did not create, the new database may not have the Logging service account listed for access. Ensure that the Logging service account has access to all newly created Logging databases.  
  
## Leading spaces not allowed in NM and SI data types  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] rejects instances of the NM and SI data types that have leading and trailing spaces.  
  
## BTAHL7 accepts a value of "0" for HL7 V2.1 SI data type  
 In the HL7 standard for HL7 V2.1, a value of "0" is not acceptable in an instance of the SI data type. However, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] accepts "0" as a valid value in an instance of the SI data type.  
  
## Mismatch of source and destination party namespaces  
 If the namespace configured in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer on the **Validation** tab does not match the source namespace in the schema for an HL7 V2.X message, the serializer may generate error messages that do not clearly identify the problem. Such error messages could indicate segment sequence errors or an unexpected end of the message body is found. If you cannot explain the cause of an error, you might check for a party namespace mismatch.  
  
## Lack of segments FTS or BTS results in error, but the message still parses  
 When the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] disassembler parses a batch message that contains the segments FHS or BHS, but does not contain the corresponding segment FTS and/or BTS, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates an error, but the message still parses.  
  
## Modifying a message header tag results in multiple errors  
 If Orchestration Designer modifies a message header tag, you may see errors that are not comprehensible, such as "invalid first segment" or "segment sequence error".  
  
## Configuration data can be affected by other BizTalk Server applications  
 If you enter custom data in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, or set configuration data programmatically through the Configuration Application Programming Interfaces (APIs), the custom data is stored in the Configuration database.  You can use the Configuration database for other party-specific information from other BizTalk applications. If another application stores data in the same location as the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration data, the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] data may not be stored correctly. If this occurs, change the storage location of the other application's data, and save the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration data again.  
  
## Errors might not be logged in the error log due to a size limitation of the event log store  
 When the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer generates a significant number of errors, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] might not log some of the errors, due to a size limitation of the event log store. You can view all of the errors in the Health and Activity Tracking (HAT) tool, but you might not be able to view all of them in the error log.  
  
## Reinstalling BTAHL7 under a different folder will cause the default receive locations not to work  
 Reinstalling BTAHL7 under a different folder will cause the default location for BatchControlPort or ports created by Launch Tutorial not to work because the URIs (as referred to in the previous installation) for these ports will not match the new folders created by the setup program. For these ports to work, you will have to update the folder path in the FILE Transport Properties dialog box for these ports.  
  
 If one or more MLLP ports exist in BizTalk when BTAHL7 is uninstalled, the MLLP adapter will not be removed. After that occurs, if you install the product at a different location, all new or old MLLP ports will stop functioning. For MLLP to work, you will have to uninstall and reinstall the MLLP adapter. For more information, see "The MLLP adapter is not removed during uninstall" in [Troubleshooting Other Issues](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-other-issues.md).  
  
## See Also  
 [Known Issues](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)