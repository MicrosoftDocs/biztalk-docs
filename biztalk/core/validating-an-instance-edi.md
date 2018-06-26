---
title: "Validating an Instance (EDI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0fe4e87-5ab4-41e4-8ceb-8f6cf40cae0b
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating an Instance (EDI)
You can validate an instance against its EDI schema at design time. To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment. The instance that you validate can be a single transaction set (without interchange and group headers), an interchange with a single transaction set (with interchange and group headers), or a complete batched interchange with multiple transaction sets (with interchange and group headers).  
  
> [!NOTE]
>  Validation of an XML preserved interchange is not supported. However, validation of an EDI preserved interchange is supported.  
  
 The validate-instance operation performs both EDI and XSD validation.  
  
 When you validate an instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] displays a dialog box in which you specify the configuration to be validated in that instance, including separators and the syntax identifier.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To validate an instance against its schema  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.  
  
2. In Solution Explorer, add to the project all schemas required for the message instance.  
  
   1. If you are validating a single transaction set without interchange and group headers, add the document schema for that transaction set.  
  
   2. If you are validating an interchange with a single transaction set, add to the project the schema for the transaction and the batch schema for the type of encoding used for the message (either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).  
  
      > [!NOTE]
      >  The batch schema is required to validate the envelope of the instance. If you were to use only the message schema, the envelope would not be validated.  
  
   3. If you are validating a batched interchange with multiple transaction sets, add to the project the schemas for each transaction set group in the message instance, and the batch schema for the type of encoding used for the message (either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).  
  
      > [!NOTE]
      >  If you have customized the service schema, you will have to include the custom service schema in the BizTalk project, in addition to the document (transaction set) schema(s) and if necessary, the batch schema.  
  
      > [!NOTE]
      >  You do not have to build the project to validate an instance.  
  
3. Display the property page for the schema in Solution Explorer, as follows:  
  
   1.  If you are validating a single transaction set, right-click the document schema for that transaction set, and then click **Properties**.  
  
   2.  If you are validating an interchange with a single transaction set or a batched interchange with multiple transaction sets, right-click the batch schema (Edifact_BatchSchema.xsd or X12_BatchSchema.xsd schema), and then click **Properties**.  
  
4. In Properties window for the schema, for **Input Instance Filename** enter the name and path of the message instance that you want to validate, or browse to the file, select it, and then click **OK**.  
  
5. For **Validate Instance Input Type**, enter the type of the file to be validate: **Native** for a EDI file or **XML** for an XML file.  
  
   > [!NOTE]
   >  Validation of an XML preserved interchange is not supported. If you select XML for the **Validate Instance Input Type** property when validating a preserved interchange, the operation will fail and nothing will be returned. However, if you select **Native** for the **Validate Instance Input Type** when validating a preserved interchange, the operation will succeed.  
  
6. Right-click the message schema (Edifact_BatchSchema.xsd or X12_BatchSchema.xsd if validating an interchange with a single transaction set or a batched interchange) and then click **Validate Instance**.  
  
7. In the **EDI Instance Properties** dialog box, do the following:  
  
   1.  If your instance should use a repetition separator, select **Repetition separator**.  
  
   2.  If your instance should use trailing delimiters, select **Yes** for **Use trailing delimiters**.  
  
   3.  If your instance should use a character set other than **Basic**, select **Extended** or **Unicode** in **Syntax identifier**.  
  
   4.  Click **OK**.  
  
       > [!NOTE]
       >  The **EDI Instance Properties** dialog box might appear a second time after you have clicked **OK**. If so, click **OK** again.  
  
       > [!NOTE]
       >  The **EDI Instance Properties** dialog box will be populated with the same values used in the last validate-instance operation that was run for the same logged-in user.  
  
8. Verify that there is a message in the **Output** window indicating that the operation succeeded.  
  
## See Also  
 [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md)   
 [Generating an Instance (EDI)](../core/generating-an-instance-edi.md)