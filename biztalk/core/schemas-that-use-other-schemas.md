---
description: "Learn more about: Schemas That Use Other Schemas"
title: "Schemas That Use Other Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Schemas That Use Other Schemas

## Overview
When your schemas become large and complex, or when the schemas that represent your different types of instance messages have some portions in common, it can be useful to combine smaller schemas into the schemas that ultimately define the structure of the instance messages you plan to exchange with trading partners. For example, you might have multiple message types that require a shipping address to be expressed within them. You can define the structure of a shipping address in a single schema, and then use that schema within other schemas that define, for example, Order, Invoice, and Shipping Notice message schemas.  

## Import, include, and redefine  
 XML Schema definition (XSD) language provides three related mechanisms for using multiple schemas together that BizTalk Editor supports. The following table summarizes the characteristics of these mechanisms, as defined by XSD.  
  
|Multischema mechanism|Usage scenario|  
|---------------------------|--------------------|  
|Import|-   Accesses and uses types defined in the imported schema.<br />-   Must use types in the imported schema as is, or derive new types from them; no type modification allowed.<br />-   Provides a mechanism for using types defined in other namespaces. Indeed, an imported schema must have a target namespace that is different from the importing schema.<br />-   Uses the **import** element and its **namespace** and **schemaLocation** attributes to reference the other schema.|  
|Include|-   Accesses and uses types defined in the included schema.<br />-   Must use types in the included schema as is, or derive new types from them; no type modification allowed.<br />-   The included schema must be in the same target namespace as the including schema, or the target namespace of the included schema must be empty.<br />-   Uses the **include** element and its **schemaLocation** attribute to reference the other schema.|  
|Redefine|-   Accesses and uses types defined in the redefined schema.<br />-   Can use types in the redefined schema as is, derive new types from them, or specify modifications to them.<br />-   The redefined schema must be in the same target namespace as the redefining schema, or the target namespace of the redefined schema must be empty.<br />-   Uses the **redefine** element and its **schemaLocation** attribute to reference the other schema. Any type redefinitions are specified with the **redefine** element. **Note:**      Using the redefine mechanism is an advanced XSD concept and should only be used after you have sufficient understanding of how and when it should be used.|  
  
> [!NOTE]
>  For complete information about the differences and similarities between the import, include, and redefine mechanisms, see the references listed in [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  

## Important details  
 To use a type defined in one schema (Schema1) within another schema (Schema2), you must provide a reference to Schema1 within Schema2. To do so, use the **Imports** property of the **Schema** node in Schema2. When you click the ellipsis (**...**) button in the **Imports** property field, the **Imports** dialog box opens. In the **Import New Schema as** drop-down list, select **XSD Import**, **XSD Include**, or **XSD Redefine**. Then click **Add** to open the **BizTalk Type Picker** dialog box and browse within your BizTalk project to select **Schema1**.  
  
 For detailed instructions about these steps, see [Creating Schemas That Use Other Schemas](../core/how-to-create-schemas-that-use-other-schemas.md).  
  
 When you use the **Imports** dialog box to import, include, or redefine another schema, one or more of the XSD elements **import**, **include**, and **redefine** is added to the XSD representation of your schema, including the appropriate attributes and attribute values. Further, in the case of the **import** element, a prefix declaration for the namespace of the other schema is added to the **schema** element.  
  
 All global types (such as **ComplexTypes**, **SimpleTypes**, element groups, attribute groups) in an imported/included/redefined schema are automatically available for use within the schema in which the former schema is imported, included, or redefined. For example, global **ComplexTypes** defined in an imported/included/redefined schema are added to the drop-down list of the **Data Structure Type** property for all of the **Record** nodes in the importing, including, or redefining schema. More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## See Also  
 [About Schemas](../core/about-schemas.md)   
 [Create Schemas That Use Other Schemas](../core/how-to-create-schemas-that-use-other-schemas.md)   
 [Create References to Another Node or Type](../core/how-to-create-references-to-another-node-or-type.md)
