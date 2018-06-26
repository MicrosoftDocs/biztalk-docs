---
title: "How to Consume Web Services in a Messaging Only Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66873959-5b1b-4d9b-ad19-f083670420b8
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Consume Web Services in a Messaging Only Scenario
One of the new enhancements for the SOAP adapter is ability to call Web services in a messaging only scenario by using content-based routing send ports. This feature makes it possible to consume Web services without creating orchestrations. It also provides better performance to consume Web services because messages do not pass through orchestrations.  
  
 To consume Web services in a messaging only scenario, do the following:  
  
-   Create a proxy library and XML schemas for invoking Web services  
  
-   Configure a send port and receive location for consuming a Web service  
  
### To create a proxy library and XML schemas for invoking Web services  
  
1. Determine the URL for the Web service.  
  
2. Open an **Empty BizTalk Server Project** in a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution. For more information about how to create a BizTalk Server project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).  
  
   > [!NOTE]
   >  This walkthrough uses a BizTalk Server project to generate proxy libraries and XML schemas that the Web service uses. You can also use the Wsdl.exe and Xsd.exe in the .NET Framework 4.0 SDK for the same purpose.  
  
3. In Solution Explorer, right-click the BizTalk Server project name, and then click **Add Service Reference**.  
  
4. In the **Add Service Reference** dialog box, click **Advanced**.  
  
5. In the **Service Reference Settings** dialog box, Click **Add Web Reference** in the **Compatibility** section.  
  
6. In the **Add Web Reference** dialog box, do the following:  
  
   1.  In the **URL** field, type a Web service URL, and then click **Go**.  
  
   2.  In the **Web reference name** field, type a name for the namespace, and then click **Add Reference**.  
  
7. The Web reference will appear under **Web References** node in Solution Explorer.  
  
   > [!TIP]
   >  Once you have a web reference added to a BizTalk project, the **Add Web Reference** command is directly available when you right-click the project name or **References** or **Web References**.  
  
8. In Solution Explorer, right-click the project name, and then click **Properties** to launch the Project Designer.  
  
9. In the Project Designer, click the **Signing** tab.  
  
10. Select **Sign the assembly** option, click the drop-down list for the **Choose a strong name key file**, and then click **Browse**.  
  
11. Browse and select the assembly key file, and then click **Open**.  
  
12. In Solution Explorer, right-click the project name, and then click **Build**.  
  
13. In Solution Explorer, right-click the project name, and then click **Deploy**.  
  
### To configure a send port and receive location for consuming a Web service  
  
1.  In the BizTalk Server Administration console, create a send port. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). When creating the send port, select SOAP as the transport type or transport protocol.  
  
2.  Configure the SOAP send port with the following settings. For more information, see [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md).  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**The following settings**|Select this option to specify the following properties.|  
    |**Assembly name**|Select the assembly created in the previous procedure. The fully qualified name of the assembly is written to the SOAP adapter **AssemblyName** property.|  
    |**Type name**|Specify the name of the class that contains the Web method to be invoked. The type name is written to the SOAP adapter **TypeName** property.|  
    |**Method name**|Specify one of the methods in the list box. The Web method is written to the Soap Adapter **MethodName** property.|  
  
    > [!NOTE]
    >  If you want to use Content-Based Routing (CBR), configure the filter of the send port. For more information, see [How to Configure Filters for a Send Port](../core/how-to-configure-filters-for-a-send-port.md).  
  
    > [!NOTE]
    >  If there is no subscriber to the response messages from the invoked Web services, a routing failure error will occur.  
  
## See Also  
 [Consuming Web Services](../core/consuming-web-services.md)