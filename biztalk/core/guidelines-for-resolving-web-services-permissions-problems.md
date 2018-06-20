---
title: "Guidelines for Resolving Web Services Permissions Problems | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e29543e9-9b87-437b-ac91-8f1cce01fab4
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Guidelines for Resolving Web Services Permissions Problems
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Web services for use with the SOAP adapter and when publishing orchestrations as Web services. This topic provides some general guidelines for minimizing Web services permissions problems and steps that you can follow to troubleshoot Web services permissions problems that affect [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## General Guidelines  
  
- **Setting user accounts**: Ensure that the IIS application host process identity associated with the virtual directory that hosts the Web service is set to a specific user account and ensure that this user account is added to the following groups:  
  
  - BizTalk Isolated Host Users (domain or local group)  
  
  - IIS_WPG (local group)  
  
    Membership in these 2 groups is required to grant the Web service created by the BizTalk Web Service Publishing Wizard the appropriate rights to publish a SOAP request message into the BizTalk MessageBox database which will in turn activate the subscribing orchestration. For more information about determining or setting the IIS application host process identity, see the **Setting IIS Application Host Process Identity** section of [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md).  
  
- **Setting permissions on the folder specified by the TEMP environment variable**: Ensure that the IIS application host process identity for the virtual directory that hosts the Web service has read and write permissions to the folder specified by the TEMP environment variable. To determine the folder that is specified by the TEMP environment variable open a command prompt on the BizTalk Server, type the following command, and then press ENTER:  
  
  ```  
  echo %TEMP%  
  ```  
  
   The folder specified by the TEMP environment variable is where the Web service is Just In Time (JIT) compiled into a dynamic link library (dll) file and therefore must be accessible with read and write permissions by this user account.  
  
- **Sending credentials in the SOAP method call**: Ensure that the Web service client is sending credentials in the SOAP method call. By default IIS 7.0 in [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] requires windows authentication. When testing a Web service with Internet Explorer, the credentials of the user who is currently logged on are automatically sent which is why the Web service may work from Internet Explorer but fail from another client. If the Web service client does not add credentials to the SOAP method call a SOAP exception will be generated due to an authentication failure. For more information about sending credentials in a SOAP method call see the sample code available in [How to use the new System.Net classes to create an HTTP client](http://support.microsoft.com/kb/303436).  
  
- **Troubleshooting errors calling a Web service**: If errors occur when calling a Web service, check the Application log, or message event and service instance tracking through the BizTalk Server Administration **Group Hub** page. For more information about the possible causes of the error, see [Monitoring BizTalk Server](../core/monitoring-biztalk-server.md) and [Using the Group Hub Page](../core/using-the-group-hub-page.md).  
  
- **Collecting debugging information**: To obtain detailed debugging information, follow the steps outlined in the topic [Debugging Published Web Services](../core/debugging-published-web-services.md) if following the steps above does not resolve the issue.  
  
## Known Issues  
 For additional information on known issues with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] related to Web services permissions, see "You cannot call an orchestration that is exposed as a Web service on a server that is running BizTalk Server" at [http://go.microsoft.com/fwlink/?LinkId=196379](http://go.microsoft.com/fwlink/?LinkId=196379).  
  
## See Also  
 [Troubleshooting BizTalk Server Permissions](../core/troubleshooting-biztalk-server-permissions.md)   
 [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md)