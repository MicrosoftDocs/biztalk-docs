---
title: "BTSTask Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c350695-13e9-441a-9f1e-03cdc3e41328
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTSTask Command-Line Reference
The topics in this section provide reference information for the BTSTask command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You can use BTSTask to perform many application deployment tasks from the command line, as follows:  
  
- Add a BizTalk application to the BizTalk Management database by using the AddApp command.  
  
- Add an artifact to an application by using the AddResource command.  
  
- Export an application and its artifacts to an .msi file by using the ExportApp command.  
  
- Export binding information to an .xml file by using the ExportBindings command.  
  
- Import an application from an .msi file by using the ImportApp command.  
  
- Import binding information from an .xml file by using the ImportBindings command.  
  
- List the artifacts included in an application along with their locally unique identifiers (LUIDs) by using the ListApp command.  
  
- List all applications in the BizTalk Management database for the BizTalk group by using the ListApps command.  
  
- List the resources in an .msi file by using the ListPackage command.  
  
- List all of the artifact types supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the ListTypes command.  
  
- Remove an application from the BizTalk Management database and the BizTalk Administration console by using the RemoveApp command.  
  
- Remove an artifact from an application by using the RemoveResource command.  
  
- Uninstall an application from the local computer by using the UninstallApp command.  
  
> [!IMPORTANT]
>  You cannot use BTSTask commands in a preprocessing or postprocessing script that will run during application import. If you do, the import may fail. This is because changes being made during import are not visible to scripts.  
  
 In addition, you can learn how to edit the console foreground colors for BTSTask. If your console background color is white, you will have difficulty reading the BTSTask console output and will need to modify the console foreground colors.  
  
> [!NOTE]
>  When a script completes, it returns a zero (0) to indicate successful completion or a non-zero number to indicate failure.  
  
## In This Section  
  
-   [AddApp Command](../core/addapp-command.md)  
  
-   [AddResource Command](../core/addresource-command.md)  
  
-   [ExportApp Command](../core/exportapp-command.md)  
  
-   [ExportBindings Command](../core/exportbindings-command.md)  

- [ExportParties Command](../core/exportparties-command.md)

- [ExportSettings Command](../core/exportsettings-command.md)
  
-   [ImportApp Command](../core/importapp-command.md)  
  
-   [ImportBindings Command](../core/importbindings-command.md)  

- [ImportParties Command](../core/importparties-command.md)

- [ImportSettings Command](../core/importsettings-command.md)
  
-   [ListApp Command](../core/listapp-command.md)  
  
-   [ListApps Command](../core/listapps-command.md)  
  
-   [ListPackage Command](../core/listpackage-command.md)  
  
-   [ListTypes Command](../core/listtypes-command.md)  
  
-   [RemoveApp Command](../core/removeapp-command.md)  
  
-   [RemoveResource Command](../core/removeresource-command.md)  
  
-   [UninstallApp Command](../core/uninstallapp-command.md)  
  
-   [How to Edit the Console Colors for BTSTask](../core/how-to-edit-the-console-colors-for-btstask.md)