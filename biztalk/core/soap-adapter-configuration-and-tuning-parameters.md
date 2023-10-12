---
description: "Learn more about: SOAP Adapter Configuration and Tuning Parameters"
title: "SOAP Adapter Configuration and Tuning Parameters"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SOAP Adapter Configuration and Tuning Parameters
You can configure the number of concurrent connections that the SOAP adapter opens for a particular destination server by making an entry in the BTSNTSvc.exe.config file that is located in the root BizTalk Server installation directory.  
  
> [!NOTE]
>  This property will be applied to both HTTP and SOAP adapters if they send messages to the same destination HTTP server. The default value for the “maxconnnection” property is 2, the maximum value that can be set for the “maxconnection” property for all URIs is 20.  
  
 The following is an example of the configuration for the maximum connections property:  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## See Also  
 [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md)   
 [HTTP Adapter Configuration and Tuning Parameters](../core/http-adapter-configuration-and-tuning-parameters.md)
