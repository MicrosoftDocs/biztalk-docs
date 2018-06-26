---
title: "Configuring Fallback Envelope Properties (X12-Transaction Set Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a951f70-07d5-4a58-b1ea-e7117a45c545
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Envelope Properties (X12-Transaction Set Settings)
In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the GS segments for an X12-encoded interchange that it sends to the party. A GS segment identifies and specifies a functional group for an X12-encoded interchange.  
  
> [!NOTE]
>  This topic applies also to HIPAA-related settings.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To define the GS segments  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.  
  
2. In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Transaction Set Settings** section, click **Envelopes**.  
  
3. For **Functional code (GS01)**, select a value from the drop-down list.  
  
4. For **Application sender (GS02)**, enter an alphanumeric value with a minimum of 2 and a maximum of 15. This is a required field.  
  
5. For **Application receiver (GS03)**, enter an alphanumeric value with a minimum of 2 and a maximum of 15. This is a required field.  
  
6. For **Date format (GS04)**, select CCYYMMDD or YYMMDD from the drop-down list. This is a required field.  
  
7. For **Time format (GS05)**, select HHMM, HHMMSS, or HHMMSSdd from the drop-down list. This is a required field.  
  
8. For **Responsible agency (GS07)**, select the value from the drop-down list.  
  
9. For **Document identifier (GS08)**, enter an alphanumeric value with a minimum of 1 and a maximum of 12. This is an optional field.  
  
10. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring X12 Fallback Agreement Properties for Transaction Set Settings](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)