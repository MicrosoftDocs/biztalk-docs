---
description: "Learn more about: Publishing from the BizTalk Server Administration Console"
title: "Publishing from the BizTalk Server Administration Console"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Publishing from the BizTalk Server Administration Console
If you want to manage endpoint publishing through the BizTalk Server Administration Console instead of the ESB Management Portal, you can do so by entering a Universal Description, Discovery, and Integration (UDDI) moniker in the description field of the endpoints to publish to UDDI. The following is an example moniker.  
  
```  
uddi://TransportType=other;Status=Published.  
```  
  
 You can set the following UDDI properties using the **Description** field in the BizTalk Server Administration Console:  
  
-   **ModifiedBy**. This optional property contains the account name of the user that modified the endpoint; for example, MyDomainName\MyUserName.  
  
-   **UDDIContact**. This optional property is the contact name of the user defined for the UDDI Business Provider.  
  
-   **UDDIUserType**. This optional property is the user type of the user defined for the UDDI Business Provider.  
  
-   **UDDIEmail**. This optional property is the e-mail address of the user defined for the UDDI Business Provider.  
  
-   **TransportType**. This optional property is the endpoint adapter type, such as **FILE, MQS, WCF-WsHttp, SOAP, HTTP,** or **FTP**.  
  
-   **Status**. This optional property is the status of the endpoint, such as **Published** or **Pending**. The UDDI Publishing Service uses this attribute to discover the status of the endpoint.  
  
-   **BindingType**. This optional property is the specific protocol (URL Type) that the UDDI binding supports, such as **mailto, http, https, ftp, fax, phone,** or **other**. The UDDI Publishing Service uses this attribute to create the endpoint binding.
