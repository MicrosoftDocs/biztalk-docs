---
title: "BTSWebSvcPub Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e19dd4d-9f2c-4a17-9437-8701e1c274fb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTSWebSvcPub Command-Line Reference
This topic provides reference information for the BTSWebSvcPub command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You can use BTSWebSvcPub to create Web services (.asmx) for publishing orchestrations through Web services as follows:  
  
## Usage  
 **BTSWebSvcPub PathName [-Location:** *value* **] [-Overwrite] [-Anonymous]**  
  
 **[-Name:** *value* **] [-Namespace:** *value* **] [-TargetNamespace:** *value* **]**  
  
 **[-UnknownHeaders[** *+* **&#124;** *-* **]] [-SingleSignOn[** *+* **&#124;** *-* **]] [-ParameterStyle:** *value* **]**  
  
 **[-ConformanceClaims:** *value* **] [-ForceRequestResponse:** *value* **] [-ReceiveLocation]**  
  
 **[-ApplicationName:** *value* **]**  
  
## Parameters  
  
|         Parameter         | Required |                                                           Description                                                            |
|---------------------------|----------|----------------------------------------------------------------------------------------------------------------------------------|
|       **PathName**        |   Yes    |                    Path and file name of BizTalk assembly (\*.dll) or web service description (\*.xml) file.                     |
|       **-Location**       |    No    |                                 Location in which to publish. (Syntax:"http://host[:port]/path")                                 |
|      **-Overwrite**       |    No    |                                                  Overwrite specified location.                                                   |
|      **-Anonymous**       |    No    |                                              Allow anonymous access to Web service.                                              |
|         **-Name**         |    No    |                    Name of the solution and assembly (.sln and .dll files) that will contain the Web service.                    |
|      **-Namespace**       |    No    |                                             Default namespace for Web service code.                                              |
|   **-Targetnamespace**    |    No    |                        Target namespace of the Web service. (Example:'<http://www.northwindtraders.com>')                        |
|    **-UnknownHeaders**    |    No    |                                                  Support unknown SOAP headers.                                                   |
|    **-SinglesSignon**     |    No    |                                  Support SharePoint Portal Server Single Sign-On SOAP headers.                                   |
|    **-ParameterStyle**    |    No    |                               The SoapParameterStyle for messages: "Default", "Bare",or "Wrapped".                               |
|  **-ConfirmanceClaims**   |    No    |                              Web services interoperability (WSI) claim: "None" or"BasicProfile1_1".                              |
| **-ForceRequestResponse** |    No    |                                Expose one-way BizTalk operations as request-response web methods.                                |
|   **-ReceiveLocation**    |    No    |                                  Create receive locations in the specified BizTalk application.                                  |
|   **-ApplicationName**    |    No    | Name of the BizTalk application in which to create receive locations. If not specified, the default BizTalk application is used. |
  
## Sample  
 BTSWebSvcPub.exe "MyAssembly.dll" -Location:<http://localhost/MyVdir>  
  
 -Overwrite  
  
## Remarks  
 Parameter names are not case sensitive and may be abbreviated. Parameter values are case sensitive.  
  
## See Also  
 [How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)