---
title: "Customizing Enumerations in the Envelope Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b053d82-753f-4a05-9922-fa5dbd073ba9
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Customizing Enumerations in the Envelope Schema
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to customize ID field enumerations in the service (envelope) schema. This enables you to receive or send interchanges that have non-standard values (outside the set of values defined by the X12 standards body) in the sender or receiver ID fields in the envelope. It also enables you to change the qualifiers that are available in drop-down lists for header values in agreement property definitions.  
  
> [!IMPORTANT]
>  When you modify a schema, that modification applies to all transactions for the standard in question. You cannot make a modification in the envelope schema for a single party.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pulls the list of allowed values from static service schemas in the Microsoft.BizTalk.Edi.BaseArtifacts.dll, which ships with the product. To extend the base set of values, you need to develop and deploy a service schema extension. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides service (envelope) schema templates that you can use to modify the enumerations in. These service schemas are X12_ServiceSchemaExtension.xsd and EDIFACT_ServiceSchemaExtension.xsd. Each custom schema will have one of the following namespaces, based upon the standard. This namespace cannot be changed.  
  
|Standard|Namespace|  
|--------------|---------------|  
|X12 and HIPAA|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006`|  
|EDIFACT|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`|  
  
 You make the changes to the schema in BizTalk Editor in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] (see the procedure below). After making the required changes, you must deploy the schema.  
  
 On both the receive and send sides, when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validates the envelope segments (ISA and GS for X12, or UNB and UNG for EDIFACT), it will check for the existence of the custom service schema based on its namespace. If the custom schema is deployed, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will merge that schema with the regular service schema and will use both custom and standard enumeration values where specified. You can customize the schema to extend an enumeration list, but you cannot remove values from it. If a custom schema is not deployed, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use the standard service schema.  
  
 After you have deployed a custom schema, the [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] user interface in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console will use the values in a custom enumeration to populate the appropriate drop-down lists in the [!INCLUDE[TPM_abbrev](../includes/tpm-abbrev-md.md)] property pages. If you have not deployed a custom schema, [!INCLUDE[TPM_abbrev](../includes/tpm-abbrev-md.md)] will use the values in the enumerations in the standard service schema. In addition, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime will use the custom enumeration to validate a message.  
  
 If you use the XML tools provided with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to validate an instance with its envelope, and you have customized the service schema, you will have to include the custom service schema in the BizTalk project, in addition to the document (transaction set) schema(s) and if necessary, the batch schema. This is not necessary if you are validating a transaction-set instance that does not have an envelope.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
##  <a name="BKMK_Env_Can"></a> Envelope Fields That Can Be Modified  
 Only the following envelope fields can be modified. Only these fields are included in the extension schemas. Added other fields in the service extension schema will not have any effect on processing.  
  
|Standard|Field|  
|--------------|-----------|  
|X12 and HIPAA|ISA01 – Authorization Qualifier<br /><br /> ISA03 – Security Qualifier<br /><br /> ISA05 – Sender ID Qualifier<br /><br /> ISA07 - Receiver ID Qualifier<br /><br /> GS01 - Functional Code<br /><br /> GS07 - Responsible Agency|  
|EDIFACT|UNB2.2 - Sender Code Qualifier<br /><br /> UNB3.2 - Receiver Code Qualifier|  
  
## Envelope Fields That Should Not Be Modified  
 Some fields in the envelope drive behaviors in the engine. As a result, you should not add values to the existing enumeration list for any of these fields. These fields are the following:  
  
|Standard|Field|  
|--------------|-----------|  
|X12 and HIPAA|ISA11 – Interchange Control Standards Identifier<br /><br /> ISA12 – Interchange Control Version Number<br /><br /> ISA14 – Acknowledgment Requested|  
|EDIFACT|UNB1.1 – Syntax Identifier<br /><br /> UNB1.2 – Syntax Version Number<br /><br /> UNB9 – Acknowledgment Request|  
  
### To customize an enumeration in the envelope schema  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a new project.  
  
2. Add the X12_ServiceSchemaExtension.xsd schema (to modify X12 or HIPAA enums) or the EDIFACT_ServiceSchemaExtension.xsd schema in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI to a BizTalk project in the BizTalk Editor. Open the schema.  
  
3. To change the values in an enumeration, select the enumeration in the **Properties** pane, and then click the ellipsis to open the **Enumeration Editor**. Add to the list of values, as needed, ensuring that there is one value on each line in the **Values** pane. Click **OK**.  
  
   > [!IMPORTANT]
   >  You cannot change the namespace for the service schema. The schema should have the same namespace and root node name as the original extension schema installed with the product.  
  
   > [!NOTE]
   >  If you were to add a new field to the schemas, that field would be ignored. Only the fields listed in the [Envelope Fields That Can Be Modified](../core/customizing-enumerations-in-the-envelope-schema.md#BKMK_Env_Can) section above can be changed.  
  
4. Save the schema.  
  
5. Right-click the schema, and click **Deploy**.  
  
   > [!NOTE]
   >  The schema must be deployed in the current BizTalk group.  
  
## See Also  
 [Developing EDI Schemas](../core/developing-edi-schemas.md)   
 [Modifying EDI Schemas](../core/modifying-edi-schemas.md)