---
description: "Learn more about: How to Change the URI of a Consumed Web Service"
title: "How to Change the URI of a Consumed Web Service"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Change the URI of a Consumed Web Service
After you deploy your orchestration, BizTalk Server configures a send port for each Web service that the orchestration references. By default, BizTalk uses the URL of the Web service at run time for the same URL for the imported Web service. You can change this URL using BizTalk Server Administration console.  
  
> [!NOTE]
>  You must deploy your orchestration before you change the URI of a consumed Web service. For more information on deploying your orchestration, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
### To change the URI of a consumed Web service using BizTalk Server Administration Console  
  
1.  In BizTalk Server Administration console, expand a BizTalk application, and then expand the **Send Ports** node.  
  
2.  Right-click a send port configured with SOAP adapter, click **Properties**.  
  
3.  If you do not have physical ports, you can create send ports and receive locations by using BizTalk Administration console. For information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
4.  On the **Send Properties** dialog box, click **Configure**.  
  
5.  In the **SOAP Transport Properties** dialog box, in the **Web Service URL** box, type the full URL for the location of the Web service, and then click **OK**.  
  
    > [!NOTE]
    >  You should ensure that a Web service exists for the URL that you specify. BizTalk Server does not validate the URL location.  
  
6.  Click OK to exit the **Send Properties** dialog box.  
  
## See Also  
 [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md)   
 [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md)   
 [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md)   
 [Creating Web Ports](../core/creating-web-ports.md)
