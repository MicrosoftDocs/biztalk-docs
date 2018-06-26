---
title: "Configuring Fallback Charset and Separator Properties (X12) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 477f4952-6a4e-4e98-a37f-f6e1fe7db3d3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Charset and Separator Properties (X12)
In the fallback agreement, you can specify the character set that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing X12 message. You can also specify what separators and terminators will be used for the segments in the interchange.  
  
> [!NOTE]
>  The settings described here also apply to HIPAA interchanges.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure the character set and separators  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.  
  
2. In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Charset and Separators**.  
  
3. From the **Character set to be used** drop-down list, select the X12 character set to be used to validate the properties that you enter for the agreement.  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] only uses this setting to validate the values entered for the related agreement properties. The receive pipeline or send pipeline will ignore this character-set property when performing run-time processing.  
  
4. For **Data element**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate composite data elements consisting of two or more simple data elements, and simple data elements that are not part of a composite element. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
5. For **Component element separator (ISA16)**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate simple data elements within composite data elements. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
6. For **Segment terminator**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to indicate the end of an EDI segment. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
7. For **Suffix**, select the character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use with the Segment identifier, either **None**, **CR** (carriage return), **LF** (line feed), or **CR LF** (carriage return/line feed). If you designate a suffix, the segment terminator data element can be empty. If the segment terminator is left empty, you must designate a suffix. The combination of the segment terminator and suffix can be any of the following:  
  
   -   Segment terminator  
  
   -   Segment terminator + carriage return  
  
   -   Segment terminator + carriage return/line feed  
  
   -   Carriage return  
  
   -   Line feed  
  
   -   Carriage return/line feed  
  
8. If the payload data contains characters that are also used as data, segment, or component separators, check **Replace separators in payload with** and specify a replacement character. When generating the outbound X12 message, all instances of separator characters in the payload data will be replaced with the specified character. Select **Char** for a character data element or **Hex** for a hexadecimal data element. The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.  
  
9. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring X12 Fallback Agreement Properties for Interchange Processing](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)