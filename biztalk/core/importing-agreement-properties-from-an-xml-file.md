---
title: "Importing Agreement Properties from an XML File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8bf5268-1742-47da-b42f-6472706a9bff
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Agreement Properties from an XML File
This section provides instructions on how to import agreement properties from an XML template file.  
  
## Prerequisites  
 The following are prerequisites for performing the procedure in this topic:  
  
- You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
- You must have exported an agreement to an XML template file, as described in [Exporting Agreement Properties to an XML FIle](../core/exporting-agreement-properties-to-an-xml-file.md).  
  
### To import agreement properties from an XML file  
  
1.  In the BizTalk Server Administration Console, click the **Parties** node under the **BizTalk Server Administration** and **BizTalk Group** nodes. In the **Parties and Business Profiles** page, create an agreement as described at [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).  
  
2.  In the **Agreement Properties** dialog box, click **Load From Template**.  
  
    > [!NOTE]
    >  The **Load From Template** button is enabled only after you select a protocol for the agreement. When you specify the protocol you also implicitly declare that you can only import an agreement for the same encoding protocol.  
  
3.  In the **Open** dialog box, browse to the location of the XML template file, select the file, and then click **Open**.  
  
4.  In the **Create Template** box, click **OK**.  
  
## See Also  
 [Reusing Properties from Another Agreement](../core/reusing-properties-from-another-agreement.md)   
 [Exporting Agreement Properties to an XML FIle](../core/exporting-agreement-properties-to-an-xml-file.md)