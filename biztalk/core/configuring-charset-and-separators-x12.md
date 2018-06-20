---
title: "Configuring Charset and Separators (X12) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6249f2e1-70b0-4960-bbc4-0c3fefd26faa
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Charset and Separators (X12)
In the partner agreement, you can specify the character set that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing X12 message. You can also specify what separators and terminators will be used for the segments in the interchange.  
  
> [!NOTE]
>  The settings described here also apply to HIPAA interchanges.  
> 
> [!IMPORTANT]
>  The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
> 
> - **Data element**  
>   -   **Component element separator (ISA16)**  
>   -   **Segment terminator**  
>   -   **Suffix**  
>   -   **Replace separators in payload with**  
> 
>   The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure the character set and separators  
  
1. Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2. On a one-way agreement tab, under **Interchange Settings** section, click **Charset and Separators**.  
  
3. From the **Character set to be used** drop-down list, select the X12 character set to be used to validate the properties that you enter for the agreement.  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] only uses this setting to validate the values entered for the related agreement properties. The receive pipeline or send pipeline will ignore this character-set property when performing run-time processing.  
  
4. For **Data element**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate composite data elements consisting of two or more simple data elements, and simple data elements that are not part of a composite element. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
5. For **Component element separator (ISA16)**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate simple data elements within composite data elements. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
6. For **Segment terminator**, enter a single character to indicate the end of an EDI segment. Select **Char** for a character data element or **Hex** for a hexadecimal data element.  
  
    If the type is **Char**, the default value is **~**.  
  
    If the type is **Hex**, the default value is **7E**.  
  
    This data element is required.  
  
    This element is limited to the values in the ASCII character set. This property is not validated against the X12 character set defined in the General page.  
  
    The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
7. For **Suffix**, select the character to use **with** the Segment Terminator value. Options include:  
  
   - **None**: Default  
  
   - **CR**: Carriage Return  
  
   - **LF**: Line Feed  
  
   - **CR LF**: Carriage Return/Line Feed  
  
     The Segment Terminator and Suffix combinations include the following:  
  
   - **Any** Segment Terminator + **None** Suffix  
  
   - **Any** Segment Terminator + **CR** Suffix  
  
   - **Any** Segment Terminator + **CR LF** Suffix  
  
   - **D (Hex)** Segment Terminator + **None** Suffix: This combination behaves as if Segment Terminator is blank and Suffix is set to CR.  
  
   - A (Hex) Segment Terminator + **None** Suffix: This combination behaves as if Segment Terminator is blank and Suffix is set to LF.  
  
   - **D (Hex)** Segment Terminator + **LF** Suffix: This combination behaves as if Segment Terminator is CR and Suffix is set to LF.  
  
8. If the payload data contains characters that are also used as data, segment, or component separators, check **Replace separators in payload with** and specify a replacement character. When generating the outbound X12 message, all instances of separator characters in the payload data will be replaced with the specified character. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
9. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md)