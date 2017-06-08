---
title: "BizTalk WCF Service Consuming Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.wcf-service.consuming.wizard"
ms.assetid: 6f4fc7b6-5a85-4c90-ae89-2933c90f7325
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk WCF Service Consuming Wizard
Use the BizTalk WCF Service Consuming Wizard to generate the BizTalk artifacts, such as BizTalk orchestrations and types, to consume a WCF service based on the metadata document of the WCF service. For general usage information about the BizTalk WCF Services Consuming Wizard, see [Using WCF Services](../core/using-wcf-services.md).  
  
## Metadata Source Page  
 Use this page to select the source of the metadata to import.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Metadata Exchange (MEX) endpoint**|Consume metadata from the metadata exchange endpoint of a running service.<br /><br /> The default value is selected.|  
|**Metadata Files (WSDL and XSD)**|Consume metadata from a set of Web Service Description Language (*.wsdl) and XML schema (\*.xsd) files.<br /><br /> The default value is cleared.|  
  
## Metadata Endpoint Page  
 Use this page to specify the Metadata Exchange (MEX) endpoint of the WCF service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Metadata Address (URL)**|Specify the URL to the running Web service that provides metadata for download through WS-Metadata Exchange or Http-Get. To get the metadata document from the URL, click **Get**.<br /><br /> The default is an empty string.|  
|**Edit**|Edit the user credential to use when downloading metadata documents from the service specified in the **Metadata Address (URL)** drop-down list. If the service requires user credentials with the basic authentication scheme, you must supply an appropriate user name and password to the service. This open the **BizTalk WCF Service Consuming Wizard** dialog box in which you can specify user name and password. **Note:**  BizTalk WCF Service Consuming Wizard does not allow you to set certificate credentials in the wizard. To workaround this limitation, see [Known Issues for the WCF Adapters](../core/known-issues-for-the-wcf-adapters.md).|  
|**Get**|Get the metadata document from the URL specified in the **Metadata Address (URL)** text box. After reviewing the metadata document, click **Next** to continue.|  
  
## Metadata Files Page  
 Use this page to specify metadata files to import.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Metadata Files**|Display the metadata files to import.|  
|**Add**|Add the metadata files to import to the **Metadata Files** view. This opens the **Add metadata files** dialog box in which you can search disk locations for metadata files. Select a complete set of WSDL and XSD files to use for metadata. You can generate these metadata files as follows:<br /><br /> svcutil.exe /t:metadata http://localhost/service.svc/mex|  
|**Remove**|Remove the metadata file selected in the **Metadata Files** view.|  
  
## Import WCF Service Metadata Summary Page  
 Use this page to review your settings. Click **Back** to make any changes to the WCF service to consume. Click **Import** to create the BizTalk artifacts to be used for consuming the WCF service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Namespace**|Specify the namespace of the managed types for the metadata files to import. This namespace appears in the orchestration and schema files that this wizard creates.<br /><br /> The default value is the name of the BizTalk project in which the BizTalk artifacts are created.|  
  
## Completing the BizTalk WCF Service Consuming Wizard Page  
 Use this page to determine if you have successfully generated the BizTalk artifacts for consuming the WCF service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Run this wizard again**|Specify whether to run this wizard again.|  
  
## See Also  
 [How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)   
 [Considerations When Consuming WCF Services with the WCF Send Adapters](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)