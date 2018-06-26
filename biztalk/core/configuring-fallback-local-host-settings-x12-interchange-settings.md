---
title: "Configuring Fallback Local Host Settings (X12-Interchange Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b552fa2b-1154-491f-9bcf-aaba3b8f343f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Local Host Settings (X12-Interchange Settings)
The local host settings govern how the EDI interchanges are processed. The settings on this page can be divided into two categories – receiver’s settings (for incoming interchanges) and sender’s settings (for outgoing interchanges). As part of the receiver’s settings, you can specify how the ST02 will be generated, the acknowledgement control number. As part of the sender’s settings, you can specify how the control numbers are generated for outgoing messages.  
  
> [!NOTE]
>  The settings described here also apply to HIPAA interchanges.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure local host – receiver’s settings  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.  
  
2. In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Local Host Settings**.  
  
3. To designate the range of transaction set control numbers used in an acknowledgment, enter values in the **ACK Control number (ST02)** fields. Enter a numeric value for the middle two fields, and an alphanumeric value (if desired) for the prefix and suffix fields. The middle fields are required and contain the minimum and maximum values for the control number; the prefix and suffix are optional. The maximum length for all three fields is nine characters.  
  
    To reset the current transaction set control number to the minimum value, click **Reset**. Check **Reset to lower limit when out of bound** to reset the control number to the lower limit once the maximum value has been exceeded.  
  
### To configure local host – sender’s settings  
  
1.  For **Interchange control number (ISA13)**, enter a range of values for the interchange control number to be used by BizTalk Server in generating an outgoing interchange. Enter a numeric value with a minimum of 1 and a maximum of 999999999. This is a mandatory field.  
  
     To reset the control number to the minimum value specified, click the **Reset** button. Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.  
  
2.  For **Group control number (GS06)**, enter the range of numbers that BizTalk Server should use for the group control number. Enter a numeric value with a minimum of one character and a maximum of nine characters. This is a required field.  
  
     To reset the group control number to the minimum value specified, click the **Reset** button. Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.  
  
3.  For **Transaction Set Control number (ST02)**, click **Apply new ID**, and then enter a range of numeric values for the required middle fields, and alphanumeric values for the optional prefix and suffix. The maximum length of all four fields is nine characters.  
  
     To reset the current transaction set control number to the minimum value, click **Reset**. Select **Reset to lower limit when out of bound** to reset the control number to the minimum value if the maximum value has been exceeded.  
  
4.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring X12 Fallback Agreement Properties for Interchange Processing](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)