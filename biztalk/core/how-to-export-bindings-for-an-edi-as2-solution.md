---
title: "How to Export Bindings for an EDI-AS2 Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 856ab630-66c4-4496-884a-fdbe641143c5
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export Bindings for an EDI-AS2 Solution
This topic describes how to export the configuration from a computer set up as an EDI and/or AS2 solution. This enables you to set up the same configuration on another computer in an automated fashion. You can export the bindings from an application, group, or assembly.  
  
 You create a binding file from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. The .xml binding file contains all information pertinent to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration. This includes all EDI and AS2 configuration properties, with the exception of certain security information. For detailed information about the nodes in a binding file (including EDI and AS2 nodes), see [Structure of a Binding File](../core/structure-of-a-binding-file.md). For general information about the EDI/AS2 bindings, see "EDI and AS2 Nodes in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Binding File" below.  
  
 You can also export bindings as part of exporting an application using an .msi file. For more information, see the [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md). Or you can use the BTSTask command to export and import bindings. For more information about BTSTask, see [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md).  
  
 **Exporting Bindings**  
  
 When you export the configuration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will automatically export the EDI Properties, and other party information, of all bound parties. If you activate the exporting of global party information, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also export properties for parties that are not bound to an orchestration, and global EDI properties. You can export global party information in three ways:  
  
- By checking the Export Global Party Information property in the Export Bindings dialog box.  
  
- By checking the Global Parties checkbox in the Select Resources pane of the Export MSI File Wizard.  
  
- By using the GlobalParties switch in the BTSTask command line tool, as follows:  
  
  ```  
  BTSTask ExportBindings -Destination:value ((([-ApplicationName:value] | [-AssemblyName:value]) [-GlobalParties]) | [-GroupLevel])  
  ```  
  
  For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] removes UNB6.1 and UNB6.2 fields from EDIFACT Properties, and ISA1, ISA2, ISA3, and ISA4 fields from X12 Properties.  
  
  In addition to using the export-bindings, export-application, or BTSTask commands, you can create an XML binding file manually. By doing so, you can export party and EDI settings from a line-of-business application. You could then import the bindings using the import-bindings command or the BTSTask command.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more information, see "Permissions Required for Deploying and Managing a BizTalk Application" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.  
  
### Exporting the Configuration into a Binding File  
  
1. On the computer that you want to export the configuration from, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
2. Right-click the BizTalk Application that you want to copy the configuration from, point to **Export**, and then click **Bindings**.  
  
   > [!NOTE]
   >  You can also use the BTSTask utility to export or import the configuration.  
  
3. Select the export option, selecting to export from the current application or group, or exporting bindings for an assembly.  
  
4. If you want to export all parties and their non-sensitive properties, even if an orchestration is not bound to them, click **Export Global Party information**.  
  
   > [!NOTE]
   >  If you do not click **Export Global Party information**, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will export properties for any parties that are bound to an orchestration, into the binding file. However, it will not export any parties that are not bound to an orchestration, unless you click **Export Global Party information**.  
   > 
   > [!NOTE]
   >  The binding file generated while the **Export Global Party information** property is selected will include the configuration of all parties defined on the computer. It is not possible to export the configuration of a subset of the complete set of parties defined on a computer.  
  
5. Click **OK** to export the bindings.  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will not export any EDI sensitive fields, such as passwords or security/authentication information. It will export a blank string for any EDI sensitive field. After importing the bindings onto another computer, you must manually set the values for EDI sensitive fields.  
  
6. Manually note any EDI sensitive fields, such as passwords or security/authentication information, for later setting on the computer that you import the bindings onto.  
  
## EDI and AS2 Nodes in the BizTalk Server Binding File  
 If you export your configuration with the **Export Global Party information** property selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a binding file that has that following nodes:  
  
```  
EdiData  
   PartyEDIProperties  
      PartnerAgreement  
         Contacts  
      PartnerEdifact  
         PartnerEdifactReceiverGroups  
         PartnerEdifactSenderGroups  
      PartnerAckValidation  
      PartnerX12  
      PartnerX12ReceiverGroups  
      PartnerX12SenderGroups  
      PartnerBatchUpdatable  
      PartnerAS2CommonUpdatable  
      PartnerAS2  
```  
  
 EDI global properties will be added to the binding file in the following nodes.  
  
```  
EDIGlobalProperties  
   EDIGlobalProperties  
      GlobalCommon  
      GlobalEdiFact  
      GlobalX12  
```  
  
 EDI and AS2 nodes are added to the end of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] binding file. The EdiData node is added to the Party subnode under the Party Collection node, and the EdiGlobalProperties node is added after, and at the same level as, the Party Collection node. For more information about the EDI and AS2 nodes in the BizTalk binding file, see [Structure of a Binding File](../core/structure-of-a-binding-file.md).  
  
 The EdiData node is optional. However, if the EdiData node is present, the subnodes under EdiData are required. Likewise, the EdiGlobalProperties node is optional; however, if the EdiGlobalProperties node is present, the subnodes under it are required.  
  
 EDI and AS2 binding file nodes do not correspond directly to the property pages in the Partner Agreement Manager in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. Some EDI and AS2 binding file nodes include properties used for sender roles and properties used for receiver roles. The role is indicated by the IsSender property in the node. For those nodes that are not used for both sender and receiver roles (PartnerAgreement, PartnerBatchUpdatable, PartnerAS2Updatable, and GlobalCommon), IsSender is always False.  
  
 The PartnerEdifact and PartnerX12 nodes contain properties for both the receiver and sender roles, whether or not IsSender is set to True or False. For example, PartnerEdifact will include a Una1 field (used for the party as an interchange receiver), even when IsSender is True. PartnerEdifact will also include a Unb5CheckDup field (used for the party as an interchange sender), even when IsSender is False. However, when IsSender is True, the fields for the party as an interchange receiver are not used in the UI or by the engine, but are given default values. Likewise, when IsSender is False, the fields for the party as an interchange sender are not used in the UI or by the engine, but are given default values.  
  
 If the default of a property is null, the field will not be included in the binding file unless that field has been given a value.  
  
 Binding file data is saved in tables of the BizTalk Management database (BizTalkMgmtDb).