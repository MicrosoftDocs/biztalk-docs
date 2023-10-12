---
title: Acknowledgment tab
description: Learn more about the Acknowledgment tab in BizTalk Server.
ms.prod: biztalk-server
ms.topic: article
ms.date: 06/08/2017
f1_keywords: 
  - "btahl7.configurationexplorer.tab.acknowledgement"
---

# Acknowledgment tab

You use the **Acknowledgment** tab to specify the acknowledgment properties for inbound and generated acknowledgments.

In the **BTAHL7 Configuration Explorer** dialog box, on the **Acknowledgments** tab, do the following:

| Use this | To do this |
|----------|------------|
| **Acknowledgment type** | Select from the following options: <br><br>- **None**. Select this option if you do not want to configure any acknowledgments. <br>- **OriginalMode**. Select this option to configure **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and the **MSH8 – Security** options only. <br>- **EnhancedMode**. Select this option to configure all available acknowledgment options. <br>- **DeferredMode**. Select this option to configure **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and the **MSH8 – Security** options only. <br>- **StaticMode**. Select this option to configure the **On success** and **On failure** acknowledgment options. |
| **MSH 15 Accept Acknowledgment Type** | Select from the following options: <br><br>- **AL**. Select this option if you always want to send accept acknowledgments. <br>- **NE**. Select this option if you never want to send accept acknowledgments. <br>- **SU**. Select this option if you want to send accept acknowledgments after successful transmission of a message. <br>- **ER**. Select this option if you want to send accept acknowledgments only in the event of an error. |
| **MSH 16 Application Acknowledgment Type** | Select from the following options: <br><br>- **AL**. Select this option if you always want to send application acknowledgments. <br>- **NE**. Select this option if you never want to send application acknowledgments. <br>- **SU**. Select this option if you want to send application acknowledgments after successful transmission of a message. <br>- **ER**. Select this option if you want to send application acknowledgments only in the event of an error. |
| **MSH1 – Field Separator** | Type a unique character as a field separator. The default value is **&#124;**, and the maximum characters allowed is one character. Note that if you need to modify MSH1, then you must use an orchestration that writes the appropriate value of MSH1 to your HL7 message context. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer reads the value from the context and uses it in the serialized message. |
| **MSH2 – Encoding Characters** | Type unique characters for the encoding characters as per the HL7 specifications. The default encoding characters are ^, ~, \\, and &. The minimum characters required are two characters, and the maximum allowed are four characters. Note that if MSH2_3 or MSH2_4 (the escape and subcomponent dynamic delimiters) are not specified in your original message, the ACK message automatically populates those fields. For example, if your original message MSH segment is `MSH&#124;^~&#124;`, where only the component and repetition delimiters are specified, then the ACK message automatically populates that field to include the third and fourth component as `MSH&#124;^~\&` if these values were not configured in the Acknowledgment sections in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer. |
| **MSH 3** | Type the field values for generated acknowledgments for the sending application. The maximum allowed length is 180 characters collectively. <br><br> When not configured, generated acknowledgments contain incoming **MSH5** message values. **Note**: This option only applies to 2.X messages. **Note**: To override the existing value to null, type **\\**. |
| **MSH 5** | Type the field values for generated acknowledgments for the destination application. The maximum allowed length is 180 characters collectively. <br><br> When not configured, generated acknowledgments contain incoming **MSH3** message values. **Note**: This option only applies to 2.X messages. **Note**: To override the existing value to null, type **\\**. |
| **MSH8 – Security** | Type an optional security character. |
| **MSH 9** | Type the field values for generated acknowledgments message type. <br><br> When not configured, generated acknowledgments contain incoming **MSH9** message values. **Note**: This option only applies to 2.X messages. **Note**: To override the existing value to null, type **\\**. |
| **MSH15 – Accept Acknowledgment Type** | Select from the following options for the accept acknowledgment type: <br><br>- **AL**. Select this option if you always want to send accept acknowledgments. <br>- **NE**. Select this option if you never want to send accept acknowledgments. <br>- **SU**. Select this option if you want to send accept acknowledgments after successful transmission of a message. <br>- **ER**. Select this option if you want to send accept acknowledgments only in the event of an error. |
| **On success** | Type the text for a static acknowledgment for a successful message delivery. |
| **On failure** | Type the text for a static acknowledgment for an unsuccessful message delivery. |
| **Route ACK to send pipeline on request-response send port** | Select this option to send a synchronous ACK message to the source LOB application. This option is only available on a solicit-response send port. <br><br> If this option is not selected, the receive pipeline generates the ACK message based upon your acknowledgment settings. |
