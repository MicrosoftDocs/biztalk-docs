---
description: "Learn more about: Developing EDI Schemas"
title: "Developing EDI Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Developing EDI Schemas
The topics in this section describe how to modify EDI Schemas for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 To use a document schema in your solution, you need to deploy the schema by adding it to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and then building and deploying the project. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will deploy the project in the default BizTalk Application 1. You can see the schemas that are deployed by opening the **Schemas** node under **BizTalk Application 1** node the **Applications** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can deploy an assembly into a different application by using the command-line deployment tool `BTSTask`.  
  
 The service and control schemas are automatically deployed by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration wizard. To see them, click the **Schemas** node in the **BizTalk EDI Application** node in the Administration Console. For more information about these schemas, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).  
  
## In This Section  
  
-   [Modifying EDI Schemas](../core/modifying-edi-schemas.md)  
  
-   [Customizing Enumerations in the Envelope Schema](../core/customizing-enumerations-in-the-envelope-schema.md)  
  
-   [Configuring Cross-Field Validation](../core/configuring-cross-field-validation.md)  
  
## See Also  
 [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md)
