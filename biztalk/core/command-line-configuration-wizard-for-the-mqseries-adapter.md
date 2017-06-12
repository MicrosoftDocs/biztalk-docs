---
title: "Command-Line Configuration Wizard for the MQSeries Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [MQSeries adapters], silent configuration"
  - "MQSeries adapters, silent configuration"
  - "configuring [MQSeries adapters], Command-Line Configuration Wizard"
  - "Command-Line Configuration Wizard"
  - "MQSeries adapters, Command-Line Configuration Wizard"
ms.assetid: cab905d1-fe19-4d6a-be1b-f561e133e1d2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Command-Line Configuration Wizard for the MQSeries Adapter
The wizard has four options for installing, uninstalling, and logging actions.  
  
## Syntax  
 **mqsconfigwiz [/u] [/i config.xml] [/l logfile] [/?]**  
  
|Option|Description|  
|------------|-----------------|  
|**/u**|Uninstalls the MQSAgent.|  
|**/i** *config.xml*|Installs the MQSAgent using the information in the file *config.xml*.|  
|**/l** *logfile*|Logs actions to the file *logfile*.|  
|**/?**|Displays a dialog box describing the command-line options.|  
  
 The contents of the XML file that contains the configuration information may vary, depending on the version of Windows you are using. For more information about the configuration file format, see [XML Configuration File for the MQSeries Adapter](../core/xml-configuration-file-for-the-mqseries-adapter.md).  
  
> [!IMPORTANT]
>  The adapter does not work while the configuration wizard is running.  
  
> [!NOTE]
>  You cannot reconfigure MQSAgent with the command-line configuration wizard. You must first run the wizard to uninstall the agent (**/u**), and then run it to configure (**/i**).  
  
## See Also  
 [Silent Configuration of the MQSeries Adapter](../core/silent-configuration-of-the-mqseries-adapter.md)