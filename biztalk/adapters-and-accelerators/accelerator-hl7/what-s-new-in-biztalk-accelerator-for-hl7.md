---
title: "New in BizTalk Accelerator for HL7 | Microsoft Docs"
description: Changes and updates with different versions of HL7 accelerator in BizTalk Server
ms.custom: ""
ms.date: "11/22/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e98595a1-2d1e-488e-8a97-7cd561948b3b
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What's new in BizTalk Accelerator for HL7
Changes and updates with the [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)]. 

## BizTalk Server 2016

|Feature|Description|  
|---|---| 
| **Initiates the connection to LOB** | Using the MLLP adapter, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] can start or initiate the connection to a remote Line of Business server (LOB) system. The LOB waits for the connection, and then sends the messages to [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] using the MLLP adapter. There are some new properties in the MLLP receive location that configure this option. See: <br/><ul><li>[Step 4 in the end-to-end tutorial](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)</li><li>[Step 4 in the interrogative tutorial](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)</li><li>[Step 5 in the interrogative tutorial](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)</li><li>[Step 4 in the batching tutorial](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)</li></ul>In [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions, the HL7 MLLP receive adapter waits for the remote LOB server to connect to the MLLP adapter, and then the LOB sends messages. <br/><br/>See [how BTAHL7 routes messages](../../adapters-and-accelerators/accelerator-hl7/how-btahl7-routes-messages.md) for more details.|

## BizTalk Server 2013 R2  
  
|Feature|Description|  
|-------------|-----------------|  
|**64-bit Support**|The MLLP adapters and the HL7 pipeline can run in both the 32-bit and 64-bit host instances.<br /><br /> The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] installation includes a 32-bit installation package and a 64-bit installation package. On a 32-bit computer, install only the 32-bit package. On a 64-bit computer, install the 32-bit **or** 64-bit package. <br/><br/>**Important:**  To use 64-bit support, only install the 64-bit package. The 64-bit package enables the adapter and pipelines to run in both 32-bit and 64-bit mode.|  
|**v2.6 Schema Support**|Support includes:<br /><br /> -   **BTAHL7V26Common** project: Includes the v2.6 schemas.<br />-   **BTAHL7Common** project: Includes the v2.6 schemas and the ACK_26_GLO_DEF acknowledgement schema; which generates the acknowledgement for v2.6 messages.<br />-   **MSH_25_GLO_DEF** schema: Handles new message header fields that are included with the v2.6 schema and continues to support all v2.*x* schemas.|  
|**Dynamic MLLP Adapter Support**|The adapter properties can be configured at Runtime using a One-Way or Two-Way (request-response) send port. See [Dynamic MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/dynamic-mllp-adapter.md).|  
|**“FreeText” Support**|If a field or segment is defined as “FreeText”, the character data in the field/segment is not parsed. See [Encoding Characters using Free Text](../../adapters-and-accelerators/accelerator-hl7/encoding-characters-using-free-text.md).|  
|**Messages with invalid MSH are sent an ACK or NACK**|Using the **ReturnErrorForInvalidMSH3** registry key, a negative acknowledgement (NACK) is sent to the party if the following occurs:<br /><br /> -   Invalid MSH3 (party is not defined in HL7 Configuration Explorer) <br />    **AND**<br />-   MSH15 and MSH16 values in the message are null or empty<br /><br /> To send the NACK, set the following registry key to 1 and then restart the host instance:<br /><br /> 32-bit host: `HKLM\SOFTWARE\Microsoft\BizTalk Accelerator for HL7`<br /><br /> 64-bit host: `HKLM\ SOFTWARE\Wow6432Node\Microsoft\BizTalk Accelerator for HL7` <br/><br/>**Tip:**  A port can subscribe to the failed message: <ul><li>Use the **BTAHL7Schemas.ParseError = True** filter condition.</li><li>Use the **Pass Through** pipeline.</li></ul>|  
|**ACK message instance remains Active**|If there is connection failure to the upstream system, the acknowledgement (ACK) sent to the upstream system remained in an Active state.<br /><br /> New Behavior: If there is connection failure to the upstream system, the ACK message is suspended.|  
|**Do not send \<SB>**|This property is added to the receive adapter port configuration properties. To enable this property, set the **UseMLLPTransACK** value:<br /><br /> -   When set to **False** (default), the adapter sends the message if the data begins with \<SB>. For example, the following message is sent:<br /> `<SB\>DataData<CR\>DataData<CR\>…`<br/><br />-   When set to **True**, the adapter sends the message if the data is missing \<SB> in the beginning. For example, the following message is sent:<br /> `DataData<CR\>DataData<CR\>…` <br/><br/>**Important:**  If a two way send port has **Do not send \<SB>** set to True, then it will not send SB with the message to the downstream system. At the same time it can receive ACK with missing SB from the downstream system.|  
|**Accept missing \<SB>**|This property is added to the send adapter port configuration properties. To enable this property, set the **UseMLLPTransACK** value:<br /><br /> -   When set to **False** (default), the adapter returns an error if the data is missing \<SB> in the beginning. For example, the following message returns an error:<br /> `DataData<CR\>DataData<CR\>…`<br/><br />-   When set to **True**, the adapter can receive the message if the data is missing \<SB> in the beginning. For example, the following messages are received:<br /> `<SB\>DataData<CR\>DataData<CR\>…` <br />`DataData<CR\>DataData<CR\>…` <br/><br/>**Important:**  If a two way receive port has **Accept Missing \<SB>** set to True, then it will accept the missing SB in the message from upstream system. At the same time it will not send SB to the upstream system.|  
  
## BizTalk Server 2013  
  
 The following enhancements were included in the previous releases:  
  
-   Recoverable Interchange support in HL7 pipeline for Batch In Batch Out Scenario.  
  
 The following feature was removed in the previous releases:  
  
-   Health Activity Tracking feature is removed from BizTalk Server and hence Auditing feature is removed from BTAHL7 but Logging remains intact.  
  
 The following feature was modified in the previous releases:  
  
-   The “Auditing and Logging service” is renamed as “HL7 Logging service”.  

## See also

[What's New in BizTalk Server 2016](../../install-and-config-guides/what-s-new-in-biztalk-server-2016.md)  
[What's New in BizTalk Server 2013 R2 and 2013](../../install-and-config-guides/what-s-new-in-biztalk-server-2013-and-2013-r2.md)