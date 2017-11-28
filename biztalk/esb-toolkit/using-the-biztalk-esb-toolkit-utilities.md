---
title: "Using the BizTalk ESB Toolkit Utilities | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2dc05ac-831a-44e1-bd44-e41398552ab1
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the BizTalk ESB Toolkit Utilities
This section describes various utilities included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 **ESB Itinerary Import Utility**  
  
 This utility is located under the \bin directory of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and is named EsbImportUtil.exe. This utility can be used to publish or deploy the itinerary XML into the ESBItineraryDB database.  
  
 The syntax for the utility is as follows:  
  
```  
>EsbImportUtil <Parameter1> <Value> <parameter2> <Value>...  
```  
  
 The various parameters it can accept are the following:  
  
 /?: \<Show the parameters help\>  
  
 /f: \<Itinerary xml file path\>  
  
 /c: \<published &#124; deployed\>  
  
 /n: \<Default Itinerary name\>  
  
 /v: \<Default Itinerary version (format 'major.minor')\>  
  
 /o: \<Silent overwrite\>  
  
 The following are examples of how to use this utility.  
  
 To publish to the Itinerary database:  
  
```  
>EsbImportUtil /f:myitinerary.xml /c:published  
```  
  
 To deploy to the Itinerary database:  
  
```  
>EsbImportUtil  /f:myitinerary.xml /c:deployed  
```  
  
 **SSO Configuration Persist Utility**  
  
 This utility is located under the \bin directory of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and is named Microsoft.Practices.ESB.PersistConfigurationTool.exe. This utility can be used to persist the ESB configuration information into the BizTalk SSO database. This can also be used to view configuration information and remove the configuration information from the SSO database.  
  
 The syntax for the utility is as follows:  
  
 **To add a configuration section:**  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /P /F:app.config /S:SectionName /A:ApplicationName  
```  
  
> [!NOTE]
>  If /S is not provided, the following sections will be added: connectionStrings, esb, esb.resolver and cachingConfiguration.  
  
 **To remove a section:**  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /R /S:SectionName  
```  
  
 To view an existing section, use the application and section switches with the /V switch.  
  
 To set the administrator group name, use the AG:AdminGroupName switch.  
  
 To set the user group name, use the UG:UserGroupName switch.