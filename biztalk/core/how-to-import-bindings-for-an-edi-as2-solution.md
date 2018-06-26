---
title: "How to Import Bindings for an EDI-AS2 Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b918fa2-44f2-4f57-95af-36858cea0d86
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Import Bindings for an EDI-AS2 Solution
This topic describes how to import the configuration of an EDI and/or AS2 solution onto another computer. Deployment of an EDI/AS2 solution is integrated with BizTalk application deployment. It is available through the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console and the BTSTask command-line tool.  
  
 You can import the configuration of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using a binding file that you created on the source computer by exporting the appropriate bindings. For information about exporting a configuration into a binding file, see [How to Export Bindings for an EDI-AS2 Solution](../core/how-to-export-bindings-for-an-edi-as2-solution.md). For information about a binding file created from a configuration, see [Structure of a Binding File](../core/structure-of-a-binding-file.md).  
  
 You can also import bindings as part of importing an application using an .msi file. For more information, see the [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). Or you can use the BTSTask command to export and import bindings. For more information about BTSTask, see the [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) topic in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help.  
  
## Prerequisites  
  
- You must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more information, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
- You must have added a reference to the **BizTalk EDI Application** from a BizTalk application that will be used as an EDI application. For instructions on adding a reference to the BizTalk EDI application, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
## Importing Bindings  
 When you import a configuration, existing EDI Properties will be overwritten. If you are importing properties for a party that has the same name as an existing party, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will override the EDI properties (or any bindings) for the existing party. In addition, if you are importing EDI global properties, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will overwrite existing EDI global properties.  
  
 After importing a configuration, you must reconfigure passwords. For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] removes UNB6.1 and UNB6.2 fields from EDIFACT Properties, and ISA1, ISA2, ISA3, and ISA4 fields from X12 Properties. After importing the bindings, you must reconfigure these sensitive fields before processing EDI messages.  
  
 If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fails to import a set of bindings, the reason could be that the Host Trusted property in the binding file is different from the Authentication Trusted property for the host. You can resolve this issue by changing the Host Trusted property in the binding file.  
  
> [!NOTE]
>  Importing a binding file from previous releases of BizTalk Server into BizTalk Server may fail. Because the partner management model has changed considerably for BizTalk Server, importing a binding file from previous BizTalk Server versions may not create the entities in BizTalk Server in accordance to the new model. For more information, see [How do Party Definitions in Previous BizTalk Server Versions Translate into the new TPM Entities?](../core/how-to-import-bindings-for-an-edi-as2-solution.md#BKMK_Party).  
  
### To import the configuration from a binding file  
  
1. On the computer that you want to import the configuration to, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
2. Right-click the BizTalk Application that you want to import the EDI/AS2 configuration into, point to **Import**, and then click **Bindings**.  
  
3. In the Import Bindings dialog box, move to the location that contains your binding file, and then click **Open**.  
  
4. After importing the bindings, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. Manually set all the EDI password fields to the appropriate values.  
  
##  <a name="BKMK_Party"></a> How do Party Definitions in Previous BizTalk Server Versions Translate into the new TPM Entities?  
 In BizTalk Server, a party definition is essentially an agreement that defines how messages are exchanged between two trading partners. In BizTalk Server, EDI and AS2 messaging has undergone a lot of change and the new Trading Partner Management (TPM) model now requires agreements to be created between two trading business profiles. So, essentially, for an agreement to exist, you first need to have defined the two trading partners, profiles for both the trading partners, and the protocol settings for both the trading business profiles. Once you have defined these entities, you can create a trading partner agreement.  
  
> [!NOTE]
>  For more information related to TPM enhancements in BizTalk Server, see [Building Blocks of a Trading Partner Management Solution](../core/building-blocks-of-a-trading-partner-management-solution.md).  
  
 Given the new TPM object model, does this mean that the EDI applications that you created in BizTalk Server cannot be migrated to BizTalk Server? The answer is no. You can reuse the existing applications from BizTalk Server 2006 R2 or BizTalk Server 2009 in BizTalk Server by using the Party Migration Tool to migrate the party data from previous BizTalk Server versions. For more information about the tool, see [Migrating EDI Artifacts from a Previous Version of BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
## See Also  
 [Importing Bindings](../core/importing-bindings2.md)