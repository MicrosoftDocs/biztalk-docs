---
title: "Configuring Cross-Field Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f0c6ae8-0b8a-4826-9dfb-bf27e5ff7fa6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Cross-Field Validation
This topic describes how to enable cross field/segment validation on transaction-set data elements in EDI-encoded messages. To do so, you need to make two settings:  
  
-   Set the cross-field validation flag in an annotation of the EDI schema. For X12 or HIPAA schemas, this is the **X12ConditionDesignator_Check** flag. For EDIFACT schemas, this is the **EdifactDependencyRule_Check** flag.  
  
-   Enable EDI-type validation in the agreement properties.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### Configuring Cross-Field Validation  
  
1. Open your schema in BizTalk Editor.  
  
2. For an X12 or HIPAA schema, find the **X12ConditionDesignator_Check** flag in an annotation in the appinfo section of the schema. Set it to **Yes**.  
  
   > [!NOTE]
   >  Setting the flag X12ConditionDesignator_Check to **Yes** cannot be performed from BizTalk Schema Editor. For setting the flag, you will have to open it in a notepad or similar text editor, edit, and then save the schema file (.xsd).  
  
3. For an EDIFACT schema, find the **EdifactDependencyRule_Check** flag in the annotation in the appinfo section of the schema. Set it to **Yes**.  
  
4. For the applicable segments of the schema, specify the relational conditions (X12 and HIPAA) or dependency rules (EDIFACT) that apply. For more information, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).  
  
   > [!NOTE]
   >  A cross-field validation condition or rule is entered for a segment in an EDI schema. If you enter a cross-field validation rule for a data element, rather than a segment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a warning when schema validation is performed.  
  
5. In the **Validation** page (under the **Transaction Set Settings** section) of the one-way agreement tab of the **Agreement Properties** dialog box for relevant agreement, make sure that the **EDI type Validation** property is selected.  
  
## See Also  
 [Developing EDI Schemas](../core/developing-edi-schemas.md)