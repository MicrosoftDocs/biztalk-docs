---
title: "Configuring Fallback Charset and Separator Properties (EDIFACT) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9eadc9c1-ebec-42f5-a9ca-06cb28bebcdf
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Charset and Separator Properties (EDIFACT)
In the fallback agreement, you can specify the character set (UNA) that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing EDIFACT message. You can also specify what separators and terminators (UNB) will be used for the segments in the interchange.  
  
 In the UNA segment, you define how BizTalk Server generates the UNA segment for an EDIFACT-encoded interchange that it sends to the party. The UNA segment defines the characters that will be used as separators and indicators for an EDIFACT-encoded interchange. Use this segment only if the interchange contains non-standard separator characters.  
  
 In the UNB segment, you define the EDIFACT character set to be used.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure the character set and separators  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.  
  
2. In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Charset and Separators**.  
  
3. In the **Syntax (UNB1)** section, do the following:  
  
   1.  For **Identifier (UNB1.1)**, enter the EDIFACT character set to be applied on the outgoing interchange. This is a required field.  
  
   2.  For **Version (UNB1.2)**, select a value between **1** and **4**. This is an optional field.  
  
4. In the **Separators** section, do the following:  
  
   1.  For **Component data element separator (UNA1)**, enter a value for the component data element separator that separates simple data elements within composite data elements. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change if you change its format.  
  
   2.  For **Data element separator (UNA2)**, enter a value for the data element separator that separates composite data elements consisting of two or more simple data elements or simple data elements that are not part of a composite. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change if you change its format.  
  
   3.  For **Decimal notation (UNA3)**, select the decimal notation to be used in the outgoing interchange.  
  
   4.  For **Release indicator (UNA4)**, enter a value for the release indicator that indicates that the following character is not a syntax separator, terminator, or release character, but is part of the original data. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change if you change its format.  
  
   5.  For **Repetition separator (UNA5)**, enter a value for the repetition separator that is used to separate segments that repeat within a transaction set. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change if you change its format.  
  
   6.  For **Segment terminator (UNA6)**, enter a value for the segment terminator that indicates the end of an EDI segment.  
  
   7.  For **UNA6 Suffix**, select the character that BizTalk Server will use with the Segment identifier, either **None**, **CR** (carriage return), **LF** (line feed), or **CR LF** (carriage return/line feed). If you designate a suffix, the segment terminator data element can be empty. If the segment terminator is left empty, you must designate a suffix. The combination of the segment terminator and suffix can be any of the following:  
  
       -   Segment terminator  
  
       -   Segment terminator + carriage return  
  
       -   Segment terminator + carriage return/line feed  
  
       -   Carriage return  
  
       -   Line feed  
  
       -   Carriage return/line feed  
  
5. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate and accept the changes and then close the dialog box.  
  
## See Also  
 [Configuring EDIFACT Fallback Agreement Properties for Interchange Processing](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)