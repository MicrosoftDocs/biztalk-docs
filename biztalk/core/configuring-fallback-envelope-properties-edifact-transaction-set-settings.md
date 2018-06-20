---
title: "Configuring Fallback Envelope Properties (EDIFACT-Transaction Set Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b56a5a93-35ac-4293-b00e-28dcd89dfa2a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Envelope Properties (EDIFACT-Transaction Set Settings)
In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the UNG segments for an EDIFACT-encoded interchange that it sends to the party.  
  
 The UNG segment is the header that identifies and specifies a functional group of an EDIFACT-encoded interchange. It contains information about the date and time that the functional group was prepared, together with the type and version of the document in the functional group.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To define the UNG segments  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.  
  
2. In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Transaction Set Settings** section, click **Envelopes**.  
  
3. For **Functional group ID (UNG1)**, enter an alphanumeric value with a minimum of one character and a maximum of six characters. This is a required field.  
  
4. Enter values to identify **Application sender (UNG2)**.  
  
   -   For **Identification (UNG2.1)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters. This is a required field.  
  
   -   For **Code qualifier (UNG2.2)**, enter an alphanumeric value with a minimum of one character and a maximum of four characters. This is an optional field.  
  
5. Enter values to identify **Application recipient (UNG3)**.  
  
   -   For **Identification (UNG3.1)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters. This is a required field.  
  
   -   For **Code qualifier (UNG3.2)**, enter an alphanumeric value with a minimum of one character and a maximum of four characters. This is an optional field.  
  
6. For **Controlling agency (UNG6)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters. This is a required field.  
  
7. Enter values to identify **Message version (UNG7)**.  
  
   -   For **Version (UNG7.1)**, enter an alphanumeric value with a minimum of one character and a maximum of three characters. This is a required field.  
  
   -   For **Release (UNG7.2)**, enter an alphanumeric value with a minimum of one character and a maximum of three characters. This is a required field.  
  
   -   For **Association assigned code (UNG7.3)**, enter an alphanumeric value with a minimum of 1 character and a maximum of 6 characters. This is an optional field.  
  
8. For **Application password (UNG8)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters. This is a required field.  
  
9. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring EDIFACT Fallback Agreement Properties for Transaction Set Settings](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)