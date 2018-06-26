---
title: "Importing Bindings2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings, requirements"
  - "importing, bindings"
  - "bindings, importing"
ms.assetid: 9e10bc04-aba8-430a-b8fd-de9399d54f88
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Bindings
The topics in this section describe how to import bindings into a BizTalk group or application.  

 When importing bindings, bear in mind the following important points:  

- **Existing bindings will be overwritten.** If the bindings that you import have the same name as existing bindings, the existing bindings are overwritten. In addition, if the binding file contains parties and aliases, any bindings for parties and aliases of the same name that already exist in the application are overwritten.  

- **All bindings in a group must be unique.** If a binding having the same name as one you are importing already exists in the group, the import operation will fail.  

- **You must reconfigure passwords.** For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file. After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function. You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location. For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

- **The host must exist in the group.** A host corresponding to the host specified in the bindings must already exist in the BizTalk group into which the bindings are imported and the host trust level must match. Otherwise, the import operation will fail.  

- **Binding import behavior depends on the source of the bindings.** The bindings may have been exported from an assembly, application, or group. Depending on from where the bindings were exported, the import operation may have different effects, as shown in the following table.  


  |        Origin of the bindings         |                                                                        Importing into an application                                                                        |                                                                                                     Importing into a group                                                                                                      |
  |---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |  Bindings exported from an assembly   | The specified application in must contain an assembly having the same name as the assembly from which the binding file was exported. Otherwise, the import operation fails. |                        The group must contain an assembly and an application having the same name as the assembly and application from which the binding file was exported. Otherwise, the import fails.                        |
  | Bindings exported from an application |            The application from which the binding file was exported must have the same name as the specified application. Otherwise, the import operation fails.            |                The application from which the binding file was exported must have the same name as an application in the group into which you are importing the bindings. Otherwise, the import operation fails.                |
  |    Bindings exported from a group     | The group from which the binding file was exported must include an application that has the same name as the specified application. Otherwise, the import operation fails.  | Bindings are imported for corresponding applications. In other words, the bindings of an application in the group from which bindings were exported are imported into an application having the same name in the current group. |


- **The Name attribute for an adapter may be incorrect.** If the binding file includes settings for an adapter, verify that the Name attribute of the TransportType element in the binding file is the same as that configured for the adapter in the BizTalk Server Administration console (under Platform Settings > Adapters).  

   In particular, you should verify that this is the case when importing bindings from [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to BizTalk Server. Some transports for which this may be an issue are as follows:  

  -   MQS  

  -   MSMQ  

  -   POP3  

  -   Windows SharePoint Services  

## In This Section  

-   [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md)  

-   [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md)  

-   [How to Import Bindings for an EDI-AS2 Solution](../core/how-to-import-bindings-for-an-edi-as2-solution.md)