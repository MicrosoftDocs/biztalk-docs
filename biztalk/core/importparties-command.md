---
title: "ImportParties Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87d43e2c-401c-4450-ad9b-2528086b99e4
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ImportParties Command
Imports the business-to-business parties and agreements from a source XML binding
  file in the configuration database, without importing any of the application
  artifacts. For more information, see **Remarks** in this topic.  

> [!IMPORTANT]
> This command is new starting with **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, and any newer versions.
> 
> [!NOTE]
>  Binding files generated in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have an application specified. They are imported into the default application.  
  
## Usage  
  **BTSTask ImportParties -Source**:*value* [**-ExcludeEdiFallbackSettings**] [**-Server**:*value*] [**-Database**:*value*]
  
## Parameters  
  
|Parameter|Required|Value|  
|---|---|---|  
|**-Source** | Required | The path and file name of the XML binding file to read.|
|**-ExcludeEdiFallbackSettings** | Optional | If specified, it excludes edi fallback (x12 and edifact) settings from the binding file.  |
| **-Server** | Optional | The name of SQL server hosting the BizTalk configuration database. |
| **-Database** | Optional | The name of the BizTalk configuration database. |

## Sample
  `BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

## Remarks
If the binding file also has application artifacts, then they are not imported. Only parties and agreements are imported.