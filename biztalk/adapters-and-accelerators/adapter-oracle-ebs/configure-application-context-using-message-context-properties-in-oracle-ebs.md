---
title: "Configure the application context using message context properties in Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51b76788-5c81-4bb4-8ef6-b1439955ea97
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the application context using message context properties in Oracle E-Business Suite
To perform operations on Oracle E-Business Suite artifacts using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must set the application context appropriately. You can set the application context in the following ways:  
  
- By specifying the binding properties that the adapter exposes. For more information, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
- By using message context properties that the adapter exposes. You must consider the following when setting the application context by using message context properties.  
  
  -   You can set values only for **ApplicationShortName**, **OrganizationID**, **ResponsibilityKey**, and **ResponsibilityName** by using message context properties. For the user name and password, you must use the binding properties. The value specified for the **ResponsibilityKey** message context property overrides the value specified for the **ResponsibilityName** message context property.  
  
  -   If you set the application context using both the binding properties and message context properties, the values specified for message context properties take precedence and override the values specified for the binding properties. However, for example, if you specify the application short name as a message context property, and the organization ID and responsibility name as binding properties, only the value for the application short name is taken from the message context property. The rest are picked from the relevant binding properties.  
  
  Why use message context properties over binding properties to set the application context? If you set the application context using binding properties, the WCF-Custom send port for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] can be used only for the specific organization ID, responsibility, and application that you specified for the binding properties. On the contrary, if you use the message context property, you can configure a “generic” WCF-Custom send port, and set the application context at the message level.  
  
  Adapter clients must set the message context properties on the message that is sent to Oracle E-Business Suite to invoke an operation on Oracle E-Business Suite. The messages in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] are immutable. Hence, clients must first create a message from the existing message, and then set the message context properties on the new message. For the procedure described in this section, assume that the existing message is called **Request**, and the new message is called **New_Request**.  
  
## Set the message context properties for BizTalk applications  
  
1. Open the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2. In Solution Explorer, right-click **References**, and then click **Add References**.  
  
3. In the **Add Reference** dialog box, click the **Browse** tab, and then browse to the location where the BizTalk property schema DLL for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is available.  
  
    This DLL, `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`, is installed by the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] at \<*installation drive*\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin.  
  
4. Select the DLL, and then click **Add**.  
  
5. In the BizTalk orchestration, add a message, **New_Request**. For the **Message Type** property, make sure you select the same type as the existing request message.  
  
6. Before the Send shape using which the message is sent to the send port, add a Construct Message shape and within that, a Message Assignment shape.  
  
7. Double-click the Message Assignment shape to open **BizTalk Expression Editor**.  
  
8. In **BizTalk Expression Editor**, add the following, and then click **OK**:  
  
   ```  
   New_Request = Request;  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ApplicationShortName) = "AR";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityKey) = "RECEIVABLES_VISION_OPERATIONS";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityName) = "Receivables, Vision Operations (USA)";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.OrganizationId) = "204";  
   ```  
  
   > [!IMPORTANT]
   >  The value specified for the **ResponsibilityKey** message context property overrides the value specified for the **ResponsibilityName** message context property.  
  
9. Make sure further processing of the orchestration is done by using the **New_Request** message.  
  
10. Before you can deploy this orchestration in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must add the assembly reference for `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll` in the BizTalk application where you will be deploying the orchestration. To deploy an assembly in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]:  
  
    1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
    2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then the application to which you want to add a BizTalk assembly.  
  
    3. Right-click **Resources**, point to **Add**, and then click **BizTalk Assemblies**.  
  
    4. In the **Add Resources** dialog box, click **Add**, navigate to the folder containing the BizTalk assembly file, which is \<*installation drive*\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin. Select the `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll` file, and then click **Open**.  
  
    5. On the **Options** tab, specify the options for installing the BizTalk assembly to the global assembly cache (GAC), and then click **OK**.  
  
## Set the Language for Performing Operations  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports the Multi-Language Support (MLS) feature of Oracle E-Business Suite, and allows you to specify a language while performing operations. The adapter exposes the **Language** message context property to specify a language for performing operations.  
  
 The value specified for the **Language** message context property overrides the value of the **Language** binding property under the **MlsSettings** binding property. For more information about the **MlsSettings** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
