---
title: "Configuring Batching Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "batching, acknowledgements"
  - "acknowledgements, batching"
ms.assetid: f3529638-e036-4270-ae6d-1bdc3ef98727
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Batching Acknowledgments
You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to specify the acknowledgment properties for inbound and generated acknowledgments.  
  
### To run BTAHL7 Configuration Explorer  
  
-   Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
### To configure message batching acknowledgments  
  
-   In BTAHL7 Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then, on the **Acknowledgments** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Acknowledgment type**|Select one of the following:<br /><br /> -   **None**. Select if you do not want to configure any acknowledgments.<br />-   **OriginalMode**. Select to configure the **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and **MSH8 – Security** options only.<br />-   **EnhancedMode**. Select to configure all available acknowledgment options.<br />-   **DeferredMode**. Select to configure the **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and **MSH8 – Security** options only.<br />-   **StaticMode**. Select to configure the **On success** and **On failure** acknowledgment options.|  
    |**MSH 15 Accept Acknowledgment Type**|Select one of the following:<br /><br /> -   **AL**. Select to always send accept acknowledgments.<br />-   **NE**. Select to never send accept acknowledgments.<br />-   **SU**. Select to send accept acknowledgments after successful transmission of a message.<br />-   **ER**. Select to send accept acknowledgments only in the event of an error.|  
    |**MSH 15 Application Acknowledgment Type**|Select one of the following:<br /><br /> -   **AL**. Select to always send application acknowledgments.<br />-   **NE**. Select to never send application acknowledgments.<br />-   **SU**. Select to send application acknowledgments after successful transmission of a message.<br />-   **ER**. Select to send application acknowledgments only in the event of an error.|  
    |**MSH1 – Field Separator**|Type a unique character as a field separator. The default value is a pipe character (**&#124;**), and the maximum characters allowed is one character. Note that if you need to modify MSH1, then you must use an orchestration that writes the appropriate value of MSH1 to your HL7 message context. The BTAHL7 serializer reads the value from the context and uses it in the serialized message.|  
    |**MSH2 – Encoding Characters**|Type unique characters as the encoding characters as per the HL7 standard. The default encoding characters are ^, ~, \\, and &. The minimum characters required are two characters, and the maximum allowed are four characters. Note that if MSH2_3 or MSH2_4 (the escape and subcomponent dynamic delimiters) are not specified in your original message, the acknowledgment (ACK) message automatically populates these fields. For example, if your original message MSH segment is `MSH&#124;^~&#124;`, where only the component and repetition delimiters are specified, then the ACK message automatically populates that field to include the third and fourth component as `MSH&#124;^~\&`, providing that the field values had not already been configured in the acknowledgment section in BTAHL7 Configuration Explorer.|  
    |**MSH3**|Type the field values for generated acknowledgments for the sending application. The maximum allowed length is 180 characters collectively.<br /><br /> When not configured, generated acknowledgments contain incoming **MSH5** message values. **Note:**  This option only applies to 2.X messages. **Note:**  To override the existing value to null, type **\\**.|  
    |**MSH5**|Type the field values for generated acknowledgments for the destination application. The maximum allowed length is 180 characters collectively.<br /><br /> When not configured, generated acknowledgments contain incoming **MSH3** message values. **Note:**  This option only applies to 2.X messages. **Note:**  To override the existing value to null, type **\\**.|  
    |**MSH8 – Security**|Type an optional security character.|  
    |**MSH15 – Accept Acknowledgment Type**|Select from the following options for the accept acknowledgment type:<br /><br /> -   **AL**. Select if you want to always send accept acknowledgments.<br />-   **NE**. Select if you never want to send accept acknowledgments.<br />-   **SU**. Select this option if you want to send accept acknowledgments after successful transmission of a message.<br />-   **ER**. Select this option if you want to send accept acknowledgments only in the event of an error.|  
    |**On Success**|Type text for static acknowledgment for a successful message delivery.|  
    |**On failure**|Type text for static acknowledgment for an unsuccessful message delivery.|  
    |**Route ACK to send pipeline on request-response send port**|Select this option to send a synchronous ACK message to the source LOB application. This option is only available on a solicit-response send port.<br /><br /> If this option is not selected, the receive pipeline generates the ACK message based upon your acknowledgment settings.|  
  
    > [!NOTE]
    >  Acknowledgments generated for a batch message with fragmentation turned off will contain MSH12.1 with value 2.4. You can manually modify the version number by applying a map in the send pipeline. For more information, see [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md).  
  
## See Also  
 [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)