---
description: "Learn more about: Writing Information to the Event Log"
title: "Writing Information to the Event Log | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d7398dc-29d8-4a7a-bab4-c8f128b47dca
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Writing Information to the Event Log
You may want to monitor the progress of the different business processes within your BizTalk application by writing information to the default Application log or to a custom event log. Writing to the event log can be useful in the following scenarios:  
  
-   You want to access application messages in a standard way using tools supplied by Windows.  
  
-   You want to archive information with other messages from the server environment for a more complete history.  
  
-   You want the ability to monitor your application using tools that interact with the event log.  
  
> [!NOTE]
>  The System.Diagnostics.EventLog.WriteEntry method has a size limitation on the message string. You will receive exception if the message string exceeds 32766 bytes.  
  
## Writing to the Application Log  
 You can write to the Application log or any other log from your code by using **System.Diagnostics.EventLog** as shown in the following:  
  
```  
System.Diagnostics.EventLog.WriteEntry("Orchestration Debug", System.String.Format("The Value = {0}", iResult));  
```  
  
 Similar, you can also do,  
  
```  
EventLog appLog = new EventLog();   
appLog.Source = "This Application's Name";  
appLog.WriteEntry("An entry to the Application event log.");  
```  
  
 If you are using a custom log, you should use the **SourceExists** method to ensure it exists before you write to it.  
  
## Writing to a Custom Log  
 Writing to a custom log is similar to writing to the Application log with the exception that you must first create the custom log. The code to create a custom log is straightforward:  
  
```  
// Create the source, if it does not already exist. if(!EventLog.SourceExists("MySource"))   
{   
  //An event log source should not be created and immediately used.  
  //There is a latency time to enable the source, it should be created  
  //prior to executing the application that uses the source.  
  EventLog.CreateEventSource("MySource", "MyNewLog");  
}  
```  
  
 However, you should not assume that your code will be run under an account that has the security privileges to create a new event log. Creating an event log takes administrator privileges and should be done in a separate utility program or, ideally, as part of an .msi installation. For more information about using custom script with an exported .msi installation, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).
