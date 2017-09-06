---
title: "Setting PeopleSoft Transport Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "setting transport properties"
  - "transport properties, setting"
ms.assetid: 44b5f015-59f1-43a3-9673-a5ba40266843
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting PeopleSoft Transport Properties
The PeopleSoft transport properties are used for design and run time. In the **Transport Properties** dialog box, you set the connection and credential parameters specific to the server system and the objects you are trying to access.  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
### To create a send port  
  
1.  Expand the Adapter Required Properties and fill in all required information for connection to the PeopleSoft server.  
  
     You must set configuration parameters to connect Microsoft BizTalk Adapter for PeopleSoft Enterprise to PeopleSoft Enterprise. This data is case sensitive.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |`Application Server Path`|A string representing the computer and port on which the PeopleSoft Application Server is running and listening. The syntax of the URL path to the PeopleSoft 8 Application is //<computer_name>:\<port>. Ask your PeopleSoft administrator for the \<port> value. The \<port> value is the JOLT protocol listener port, not the App Server port. The default JOLT port is 9000.|  
    |`JAVA_HOME`|Set the JAVA_HOME variable to point to your JDK installation, for example: **C:\j2sdk1.4.2_08**.|  
    |`Password`|If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.<br /><br /> A string representing the user's password for logon to a PeopleSoft system. The characters do not appear but are represented by asterisks (*).|  
    |`PeopleSoft 8.x Jar Files`|To use Ccmponent interfaces (PeopleSoft 8 only) you must update your CLASSPATH to include the PeopleSoft Component Interface jar file. For example: **<PeopleSoft_Home>\web\PSJOA\psjoa.jar**.|  
    |`User Name`|If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.<br /><br /> A string representing a user name required for logon to a PeopleSoft system.|  
  
2.  Enter an **Additional parameters** value when a date is used as a key; it has a different format. YYYY-MM-DD is the default format.  
  
3.  Enter a **Concurrency control** value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.  
  
     The **Max Concurrent Calls** parameter activates an overload protection if the back-end server cannot process the amount of data. A concurrent call is a request for which the adapter does not yet have a reply. Set **Max Concurrent Calls** in instances where the throughput exceeds back-end processing capabilities.  
  
     The default value for this field is -1, meaning no protection occurs.  
  
     If BizTalk Server submits a request to the Transmit adapter, and the number of concurrent calls equals or exceeds the value set for **Max Concurrent Calls**, the thread submitting the request is saved until the concurrent calls number decreases to below the set value.  
  
## See Also  
 [Creating PeopleSoft Send Handlers](../core/creating-peoplesoft-send-handlers.md)