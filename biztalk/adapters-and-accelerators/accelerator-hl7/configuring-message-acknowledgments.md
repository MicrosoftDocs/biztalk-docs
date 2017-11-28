---
title: "Configuring Message Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "acknowledgements, configuring"
  - "messages, acknowledgements"
  - "configuring, acknowledgements"
ms.assetid: 6ebcfc32-0a0b-4388-938f-6569a2014b91
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Message Acknowledgments
You use the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer **Acknowledgment** tab to specify the acknowledgment properties for inbound and generated acknowledgments.  
  
 The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Acknowledgment** tab.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-ack.gif "hl7_ops_ack")  
  
 Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and configure message acknowledgments.  
  
### To open BTAHL7 Configuration Explorer  
  
-   Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
### To configure message acknowledgments  
  
1.  In BTAHL7 Configuration Explorer, on the **Parties** tab, select the party you want to configure, and then on the **Acknowledgments** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Acknowledgment type**|Select from the following options:<br /><br /> -   **None**. Select this if you do not want to configure any acknowledgments.<br />-   **OriginalMode**. Select this option to configure **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and **MSH8 – Security** options only.<br />-   **EnhancedMode**. Select this option to configure all available acknowledgment options.<br />-   **DeferredMode**. Select this option to configure **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and **MSH8 – Security** options only.<br />-   **StaticMode**. Select this option to configure the **On success** and **On failure** acknowledgment options.|  
    |**MSH 15 Accept Acknowledgment Type**|Select from the following options:<br /><br /> -   **AL**. Select this option if you always want to send accept acknowledgments.<br />-   **NE**. Select this option if you never want to send accept acknowledgments.<br />-   **SU**. Select this option if you want to send accept acknowledgments after successful transmission of a message.<br />-   **ER**. Select this option if you want to send accept acknowledgments only in the event of an error.|  
    |**MSH 16 Application Acknowledgment Type**|Select from the following options:<br /><br /> -   **AL**. Select this option if you always want to send application acknowledgments.<br />-   **NE**. Select this option if you never want to send application acknowledgments.<br />-   **SU**. Select this option if you want to send application acknowledgments after successful transmission of a message.<br /><br /> **ER**. Select this option if you want to send application acknowledgments only in the event of an error.|  
    |**MSH1 – Field Separator**|Type a unique character as a field separator. The default value is a pipe character (**&#124;**), and the maximum characters allowed is one character. Note that if you need to modify MSH1, then you must use an orchestration that writes the appropriate value of MSH1 to your HL7 message context. The BTAHL7 serializer reads the value from the context and uses it in the serialized message.|  
    |**MSH2 – Encoding Characters**|Type unique characters as the encoding characters as per the HL7 standard. The default encoding characters are ^, ~, \\, and &. The minimum characters required are two characters, and the maximum allowed are four characters. Note that if MSH2_3 or MSH2_4 (the escape and subcomponent dynamic delimiters) are not specified in your original message, the ACK message automatically populates those fields. For example, if your original message MSH segment is `MSH&#124;^~&#124;`, where only the component and repetition delimiters are specified, then the ACK message automatically populates that field to include the third and fourth component as `MSH&#124;^~\&` if these values were not configured in the Acknowledgment sections in BTAHL7 Configuration Explorer.|  
    |**MSH 3**|Type the field values for generated acknowledgments for the sending application. The maximum allowed length of 180 characters collectively.<br /><br /> When not configured, generated acknowledgments contain incoming **MSH5** message value. **Note:**  This option only applies to 2.X messages. **Note:**  To override the existing value to null, type **\\**.|  
    |**MSH 5**|Type the field values for generated acknowledgments for the destination application. The maximum allowed length of 180 characters collectively.<br /><br /> When not configured, generated acknowledgments contain incoming **MSH3** message value. **Note:**  This option only applies to 2.X messages. **Note:**  To override the existing value to null, type **\\**.|  
    |**MSH8 – Security**|Type an optional security character.|  
    |**MSH 9**|Type the field values for generated acknowledgments message type.<br /><br /> When not configured, generated acknowledgments contain incoming **MSH9** message value. **Note:**  This option only applies to 2.X messages. **Note:**  To override the existing value to null, type **\\**.|  
    |**MSH15 – Accept Acknowledgment Type**|Select from the following options for the accept acknowledgment type:<br /><br /> -   **AL**. Select this option if you always want to send accept acknowledgments.<br />-   **NE**. Select this option if you never want to send accept acknowledgments.<br />-   **SU**. Select this option if you want to send accept acknowledgments after successful transmission of a message.<br />-   **ER**. Select this option if you want to send accept acknowledgments only in the event of an error.|  
    |**On Success**|Type the text for a static acknowledgment for a successful message delivery.|  
    |**On failure**|Type the text for a static acknowledgment for an unsuccessful message delivery.|  
    |**Route ACK to send pipeline on request-response send port**|Select this option to send a synchronous ACK message to the source LOB application. This option is only available on a solicit-response send port.<br /><br /> If this option is not selected, the receive pipeline generates the ACK message based upon your acknowledgment settings.|  
  
2.  Click **Save**.  
  
## See Also  
 [ACK Configuration Settings](../../adapters-and-accelerators/accelerator-hl7/ack-configuration-settings.md)   
 [Acknowledgment Settings](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)   
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)