---
title: "Modifying EDI Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fa33c5e-17ca-4aaf-a1ca-1972a9bb45ac
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Modifying EDI Schemas
You can modify an existing EDI schema that is shipped in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. When you and your trading partners have agreed on modifications to standard schemas, and perhaps changed the relevant Message Implementation Guideline (MIG) file, you can modify the schemas in the BizTalk Editor in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  Some schema modifications (cross-field validation and HIPAA subdocument splitting) involve changes to the annotations in an EDI schema. These changes cannot be made in BizTalk Editor, but can be made in a text editor, such as Notepad.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
## Schema Naming Convention  
 An EDI schema is identified by its root name and its namespace. You cannot deploy two schemas in the same BizTalk Group with the same root name and namespace. You cannot modify the root name of any EDI schema, or add to the root name, because the root name must contain the version and the document type in a standard naming convention. As a result, if you want to deploy two schemas in the same BizTalk Group with the same root name, you must use a different namespace for each one.  
  
 It is not uncommon for a company to deploy in the same BizTalk Group a different version of the same schema for two or more different trading partners. In this case, the two schemas would have the same version and the same document type. To deploy these two schemas, you would have to have different namespaces for each schema.  
  
## EDI Schema Changes  
 You can make the following changes to an EDI schema in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]:  
  
|To do this|Do this|  
|----------------|-------------|  
|Change an enumeration<br /><br /> (such as the list of values in a code list)|In the properties for an element, open the **Enumeration Editor** and add a value to, or delete a value from, the enumeration list.|  
|Change the optionality of a data element|Change the **Min Occurs** property. Change it to 0 to make the field optional or to 1 to make it required.|  
|Change the maximum number of times that a data element can appear in the file|Change the **Max Occurs** property.|  
|Change the number of characters in the data element|Change the **Length** property.|  
|Change the data type of a data element|Change the **Base Data Type** or **Date Type** property.|  
|Add a custom field|Insert a child field element schema node and set its properties. **Note:**  Adding a child field attribute to a record in an EDI schema is not allowed, because the sequence of the elements would not be guaranteed. Trying to add a child field attribute results in an invalid schema. You can only add a child field element to a record in an EDI schema.|  
|Add a custom record|Insert a child record schema node, set its properties, and then add child field elements.|  
|Delete a custom field or record|Delete a custom field or a custom record with its child field elements.|  
|Enable cross-field validation|Set the cross-field validation flag in the annotation in the appinfo section of the schema to **Yes**. This flag is either **X12ConditionDesignator_Check** (for X12 or HIPAA schemas) or **EdifactDependencyRule_Check** (for EDIFACT schemas).<br /><br /> Enable cross-field validation for a specific element by specifying the relational conditions (X12 and HIPAA) or dependency rules (EDIFACT). For more information, see [Configuring Cross-Field Validation](../core/configuring-cross-field-validation.md).<br /><br /> You also need to set the **Edi type validation** property to **yes**.<br /><br /> Cross-field validation is enabled by default for HIPAA schemas.|  
|Enable HIPAA subdocument splitting|In one of the HIPAA schemas that you can set subdocument splitting in, set the **subdocument_break** and **Split_Without_Sibling_Data** properties for the schema to **yes** and the **subdocument_creation_break** property for a specific element in the schema to **yes**.<br /><br /> You also need to set the **Inbound batch processing option** agreement property to **Split Interchange as Transaction Sets**.<br /><br /> For more information, see [Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md).|  
|Add trigger fields to a HIPAA document|You can allow the EDI disassembler to create unique XML records for a segment of your HIPAA document, based on a qualifying element known as a trigger field. You must specify the attributes that describe the segment and the trigger value so a unique XML record is created for the segment. For more information, see [HIPAA Schema Trigger Field Annotations](../core/hipaa-schema-trigger-field-annotations.md).|  
|Add a segment to an X12 transaction set|When you add a new segment to an X12 transaction set, the first three characters of the segment name are used as the segment identifier. Hence, we recommend that you name a segment such that the first three characters are unique.|  
|Add a loop to a HIPAA transaction set|When you add a new loop to a HIPAA transaction set, we recommend naming the loop to include “Loop” within the name. An example format for a loop is “TS837_2010AB_Loop”. **Note:**  The first segment in a loop is mandatory (minOccurs of the segment must be equal to 1) in order to avoid ambiguity.|  
|Add an ‘any order loop’ to a HIPAA transaction set|When a transaction set has equivalent segments with different semantics, you must define them in a SubLoop. A SubLoop with XML annotation of \<xs:all\> allows equivalent segments to occur in any order.<br /><br /> We recommend that you name an ‘any order loop’ to include “SubLoop” in the loop name. An example format is “TS837Q1_2010A_SubLoop” **Note:**  The elements of an any order loop must only occur once within the loop. The siblings of a SubLoop must have a maxOccurs set to 1, in order to avoid ambiguity.|  
  
### To modify an existing EDI schema in BizTalk Editor  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], add the schema that you want to modify to a project and open the schema in BizTalk Editor.  
  
   > [!NOTE]
   >  You can display the schema in graphical form by clicking the **EDI** tab at the bottom of the Schema Editor screen. It is much easier to navigate the nodes of the schema using this tabular format.  
  
2. To change the properties of a data element or record, click the appropriate node in the left pane of BizTalk Editor and change its properties in the Properties window.  
  
3. To change the values in an enumeration, select the enumeration in the **Properties** pane, and then click the ellipsis to open the **Enumeration Editor**. Add to or delete from the list of values, as needed, ensuring that there is one value on each line in the **Values** pane. Click **OK**.  
  
4. To add a custom field to the schema, right-click a record node in the console tree of BizTalk Editor, point to **Insert Schema Node**, and click **Child Field Element**. Name the data element, and then drag the data element to the appropriate position in the record. Set the properties for the custom field properties as required.  
  
   > [!NOTE]
   >  Adding a child field attribute to a record in an EDI schema is not allowed, because the sequence of the elements would not be guaranteed. Trying to add a child field attribute results in an invalid schema.  
  
5. To add a custom record to the schema, right-click a record node in the console tree of Schema Editor, point to **Insert Schema Node**, and then click **Child Record**. Name the record, and then drag the record to the appropriate position in the schema. Add at least one data element to the record. Set the properties for the custom record as required.  
  
6. After making the desired changes to the schema, you can change the target namespace that applies to the schema property by clicking the root node (\<Schema\>) and then changing the **Target Namespace** property.  
  
7. Save the schema.  
  
8. Validate the schema by right-clicking the schema in Solution Explorer and clicking **Validate Schema**.  
  
   > [!NOTE]
   >  The **Validate Schema** command will validate the EDI schema because the **Schema Editor Extension** property of the root node (\<Schema\>) is set to **EDI Schema Editor Extension**.  
  
### To modify annotation properties in an existing EDI schema  
  
1.  Open the schema in a text editor such as Notepad.  
  
2.  To enable cross-field validation, proceed as follows. For more information, see [Configuring Cross-Field Validation](../core/configuring-cross-field-validation.md).  
  
    1.  In the appinfo annotation at the top of the schema, set the cross-field validation flag (either **X12ConditionDesignator_Check** for X12 or HIPAA schemas or **EdifactDependencyRule_Check** for EDIFACT schemas) to **Yes**.  
  
        > [!NOTE]
        >  The cross-field validation flag is **Yes** by default for BizTalk Server HIPAA schemas.  
  
    2.  In the annotation for a specific element, specify the relational conditions (X12 or HIPAA) or dependency rules (EDIFACT) for the element. For more information about these settings, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).  
  
        > [!NOTE]
        >  In the **Validation** page (under the **Transaction Set Settings** section) of the one-way agreement tab of the **Agreement Properties** dialog box for relevant agreement, make sure that the **EDI type Validation** property is selected.  
  
3.  To enable HIPAA subdocument splitting, proceed as follows. For more information, see [Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md).  
  
    1.  In the appinfo annotation at the top of the schema, set the **subdocument_break** and **Split_Without_Sibling_Data** flags to **yes**.  
  
    2.  In the appinfo annotation for a specific element, see the **subdocument_creation_break** flag to **yes**.  
  
        > [!NOTE]
        >  In the **Local Host Settings** page (under the **Interchange Settings** section) of the one-way agreement tab of the **Agreement Properties** dialog box for the relevant agreement, make sure that the **Inbound batch processing option** property is set to **Split Interchange as Transaction Sets**.  
  
## See Also  
 [Developing EDI Schemas](../core/developing-edi-schemas.md)