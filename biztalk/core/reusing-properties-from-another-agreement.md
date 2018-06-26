---
title: "Reusing Properties from Another Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8e1cc60-d581-43ca-aa70-1e0d6238497a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Reusing Properties from Another Agreement
You can reuse properties between agreements. This can save a significant amount of time when either most or all of the properties of a new agreement are the same as those of an existing agreement. The [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] user interface in BizTalk Server enables you to export an agreement into an XML template file. You can then import the XML template to reuse the same agreement properties.  
  
 Exporting the agreement to an XML template captures most, but not all, properties from the agreement. The following properties will *not* be exported to the XML template file:  
  
- All the properties from the **General Properties** page in the **General** tab.  
  
- All the properties from the **Contacts** page in the **General** tab.  
  
- All the properties from the **Additional Properties** page in the **General** tab.  
  
- Identifier-related settings from the **Identifiers** page in the one-way agreement tab. These are:  
  
  -   **For X12**: ISA5, ISA6, ISA7, ISA8, and additional agreement resolver settings  
  
  -   **For EDIFACT**: UNB 2.1, UNB 2.2, UNB 3.1, UNB 3.2, and additional agreement resolver settings  
  
  -   **For AS2**: AS2-To, AS2-From, and additional agreement resolver settings  
  
- Send port association from the **Send Ports** page in the one-way agreement tab for X12, EDIFACT, and AS2 agreements.  
  
  Other than the properties listed above, the following properties will be exported to the XML template file:  
  
- All settings related to the encoding protocol (X12, EDIFACT, or AS2).  
  
- All the batch-related settings (other than the batch ID).  
  
> [!NOTE]
>  All the applicable properties will be overwritten when you copy properties to the destination agreement.  
  
## In This Section  
  
-   [Exporting Agreement Properties to an XML FIle](../core/exporting-agreement-properties-to-an-xml-file.md)  
  
-   [Importing Agreement Properties from an XML File](../core/importing-agreement-properties-from-an-xml-file.md)  
  
## See Also  
 [Configuring EDI Properties](../core/configuring-edi-properties.md)