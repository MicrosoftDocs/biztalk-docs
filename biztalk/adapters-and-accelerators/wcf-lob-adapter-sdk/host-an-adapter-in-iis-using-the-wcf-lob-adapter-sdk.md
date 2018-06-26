---
title: "Host an adapter in IIS using the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 90b6cd97-01b3-4c98-a190-c6e0ccf24d2b
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Host an adapter in IIS using the WCF LOB Adapter SDK
This section contains information about hosting an adapter built by using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] in Internet Information Services (IIS). For more information about other hosting options, see [Hosting Services](https://msdn.microsoft.com/library/ms730158.aspx).

## Use IIS and ASP.NET
 You can use IIS with ASP.NET enabled to publish adapters created with the WCF LOB Adapter SDK. To host an adapter created by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you configure Internet Information Services (IIS) for publishing WCF services. Next, consider how to use your WCF adapterwith ASP.NET.

 When hosting a WCF service in IIS, there are two hosting modes available: **side-by-side** and A**SP.NET compatibility mode**. The default hosting mode is side-by-side. Side-by-side mode behaves consistently with other WCF hosting solutions. Therefore, a WCF service hosted in IIS behaves the same as one hosted in a console application. However, this may not be desirable because web developers might expect behavior similar to ASP.NET. For instance, in side-by-side mode, WCF does not adhere to any URL-based authorization rules specified in the `<system.web> <authorization>` configuration element of web.config.  

 ASP.NET compatibility mode allows the WCF service to use all the features of ASP.NET, and to behave the same as an ASPX page; however, you must take additional steps when creating your WCF adapter to enable this functionality. For more information, see: 

 [WCF Services and ASP.NET](https://msdn.microsoft.com/library/aa702682.aspx)

[Hosting in Internet Information Services](https://msdn.microsoft.com/library/ms734710.aspx)

[WCF Hosting Services](https://msdn.microsoft.com/library/ms730158.aspx)

## Use the WCF Adapter Service Development Wizard

Use the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] to automate creation of a Web project for hosting your adapter within Internet Information Services (IIS). The hosted adapter can then be consumed by clients using Windows Communication Framework (WCF) or Web services.  

### Publish an adapter as a WCF service hosted in IIS  

1. Open [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]. On the **File** menu, select **New**, and then select **Web Site**.  

2. In **Templates**, select **Visual C#**, and select **WCF Adapter Service**.  

3. Enter the folder to save the solution, and then select **OK**. The **WCF Adapter Service Development Wizard** starts.  

4. On the **Introduction** page, click **Next**.  

5. On the **Choose Operations** page, specify the binding, contract, and operations to use for this hosted service.  

   1.  In the **Select a binding** list, select the adapter binding to use, and then click **Configure**. This displays the **Configure Adapter** dialog box. Provide the values necessary to invoke the adapter and to retrieve operation metadata.  

   2.  On the **Security** tab, select the **Client credential type** to use when passing client credentials to the adapter.  

       |Credential Type|Description|  
       |---------------------|-----------------|  
       |**None**|The client does not need to present credentials.|  
       |**Windows**|The client will use Windows credentials.|  
       |**Username**|The client will supply a user name and password.|  
       |**Certificate**|The client will be authenticated by using an X.509 certificate. If this value is set, click **Browse** in the **Client Certificate** area, and then select the certificate to use.|  

   3.  On the **URI Properties** tab, specify the URI parameters required by the adapter. The entries displayed in this tab vary based on the properties exposed in the  `ConnectionUri Properties` class of the adapter.  

   4.  On the **Binding Properties** tab, specify values for the binding properties required for the adapter. The **General** section contains common settings such as timeout values. Additional properties are listed based on the custom properties exposed in your `AdapterBinding` class.  

6. Once you have specified the configuration values, click **Connect**.  

   1.  From the **Select contract type** list, select the contract to use. This populates the **Select a category** tree control with a list of categories and operations available from this adapter. If the adapter implements search functionality through a `MetadataRetrievalClient` class, you can enter a search term in the **Search in category** field to return only categories and operations that contain the search term.  

       > [!NOTE]
       >  Only outbound operations are available for selection.  

   2.  From the **Available categories and operations** box, select the items to add, and then click **Add**. Once you have added the desired items, click **Next**.  

7. On the **Configure Service and Endpoint Behaviors** page, set the desired behaviors for this adapter.  

   1.  The **Service Behavior Configuration** section contains entries that control the service behavior. After running the wizard, you can modify the selected service behaviors by editing the web.config file.  

       |Property|Description|  
       |--------------|-----------------|  
       |**EnableMetadataExchange**|Setting this value to **True** enables service metadata publishing to client requests. This can also be set by modifying \<**serviceMetadata httpGetEnabled=””**\> in web.config. Default is **False**|  
       |**IncludeExceptionDetailsinFault**|Setting this value to **True** results in managed exception information returned to the client in SOAP faults. This can also be set by modifying \<**serviceDebug usingincludeExceptionDetailInFaults=””**\> in web.config. Default is **False**.|  
       |**Name**|Name for the service behavior configuration.|  
       |**UseServiceCertificate**|This value determines whether the service will use an X.509 certificate to authenticate itself to the client process. Default is **True**.|  
       |**FindValue**|This value is used to search for a specific X.509 certificate in the certificate store. This can also be set by modifying \<**serviceCredentials findValue=””**\> in web.config **Note:**  Specify a value for this property only if **UseServiceCertificate** is set to **True**.|  
       |**StoreLocation**|This value specifies system store location to search for the specified certificate. This can also be set by modifying \<**serviceCredentials storeLocation=””**\> in web.config. **Note:**  Specify a value for this property only if **UseServiceCertificate** is set to **True**.|  
       |**StoreName**|This value specifies the specific system store to search for the specified certificate. This can also be set by modifying \<**serviceCredentials storeName=””**\> in web.config **Note:**  Specify a value for this property only if **UseServiceCertificate** is set to **True**.|  
       |**X509FindType**|The type of search to use with the FindValue specified earlier in order to find the specific certificate to use. This can also be set by modifying \<**serviceCredentials x509FindType=””**\> in web.config **Note:**  Specify a value for this property only if **UseServiceCertificate** is set to **True**.|  

   2.  The **Endpoint Behavior Configuration** section controls the endpoint behavior.  

       |Property|Description|  
       |--------------|-----------------|  
       |**Name**|The name of the endpoint behavior|  
       |**AuthenticationType**|This value instructs the adapter where to obtain the client credentials of the incoming document. To enable clients to specify a client certificate to authenticate to the service, set this to **ClientCredentialUsernamePassword**. To enable clients to specify the user name and password as part of the HTTP header, set this to **HTTPUsernamePassword**. To enable clients to specify credentials through the ClientCredential interface, set this to **Auto**. If this fails, clients can pass credentials as part of the HTTP header.<br /><br /> This value can also be set by modifying \<**endpointBehavior adapterSecurityBridgeType**\> in web.config. Default is **Auto**.|  
       |**UsernameHeader**|This specifies the name of the header that will be used to pass the user name to the service. For more information about HTTP headers, see “Support for Custom HTTP and SOAP headers” at [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> This value can also be set by modifying \<**endpointBehavior usernameHttpHeader**\> in web.config. **Note:**  You must specify a value for this property if the **AuthenticationType** is set to **HTTPUserNamePassword**.  If set to **Auto**, this property is optional.|  
       |**PasswordHeader**|This specifies the name of the header that will be used to pass the user password to the service. For more information about HTTP headers, see “Support for Custom HTTP and SOAP Headers” at [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> This value can also be set by modifying <**endpointBehavior passwordHttpHeader**< in web.config. **Note:**  You must specify a value for this property if the **AuthenticationType** is set to **HTTPUserNamePassword**. If set to **Auto**, this property is optional.|  

   3.  After setting the desired behavior, click **Next** to continue.  

8. On the **Configure Service Endpoint Binding and Address** page, you can configure the address and binding properties for the contracts. Select the contract in the **Select a contract to configure** list, and then enter the desired values in the **Configure the address and binding for the contract** dialog box.  

   1.  Select the **BindingConfiguration** entry under Binding Properties. The wizard only supports basic HTTP binding so the binding configuration field is automatically set to **System.ServiceModel.Configuration.BasicHttpBindingElement**. To change the configuration properties for this binding, click the ellipsis **…** button. To use a secure communication channel, you must always set the **Mode** property to **Transport**. This is the default value.  

   2.  Select the **EndpointName**, and then enter the desired name of the endpoint.  

   3.  To apply your changes, click **Apply**.  

9. To continue, click **Next**. The Summary page lists a tree structure of the adapter operations that were selected.  

10. Review the summary, and then click **Finish**.  

11. The wizard creates a Web project and adds the following files.  


    |    File    |                                                Description                                                 |
    |------------|------------------------------------------------------------------------------------------------------------|
    |    .svc    |                               Service file that references to the WCF proxy.                               |
    |    .cs     |                                         Implements the WCF proxy.                                          |
    | web.config | Contains \<**endpoint**\, \<**bindings**\>, and \<**behaviors**\> elements for \<**system.ServiceModel**\> |


12. Publish the WCF service project.  

    1.  Right-click the project in Solution Explorer, and then click **Publish**.  

    2.  In the **Publish Web Site** dialog box, specify the target URL for the WCF service.  

    3.  Select **Allow this precompiled site to be updated**.  

    4.  Select **Use fixed naming and single page assemblies**.  

    5.  Select **Enable strong naming on precompiled assemblies**, and then specify the signing key to use.  

13. To publish the Web site, click **OK**.  

14. Verify that the service is published successfully.  

    1.  Start the IIS Management Console.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services**.  

    2.  Navigate to the node where you published the service.  If the service was published as http://localhost/myservice, navigate to **Internet Information Services**> **Computer Name**> **Web Sites**> **Default Web Site**> **myservice**.  

    3.  On the right pane, right-click the .svc file, and then click **Browse**. The Web page shows up with information about the service. You can now consume this service by using WCF or Web service calls from client applications. 

## Security
When the adapter is hosted within a service, calls from client applications use the Adapter Security Bridge to pass client credentials to the adapter.  

 When a WCF client sends authentication to a WCF service, normally the service consumes the authentication. However, in the case of an adapter, the idea is to capture the authentication information for use with the underlying LOB system. This is implemented through the Adapter Security Bridge, which is surfaced as an endpoint behavior. As an adapter developer, there is nothing that needs to be implemented to take advantage of this functionality; however, when deploying the adapter, you must consider how the client will be providing credentials to the service.  

 If you are using message-level security, the Adapter Security Bridge can retrieve the ClientCredentials sent by the client application on any binding. If you are using basic HTTP binding, you can instead select to use a custom header to pass the user name and password information. It is recommended to use the ClientCredential class provided by WCF to pass credentials, however many Web Service client applications will need to use a custom header to pass credentials.  

 The following is an example configuration where the adapter looks for credentials in the ClientCredentials that the client application provides. If none is found, the adapter then looks in the HTTP request headers that are specified.  

```  
<endpointBehaviors>  
   <behavior name="customEndpointBehavior">  
      <endpointBehavior usernameHttpHeader="UNHdr" passwordHttpHeader="PWHdr"  
         adapterSecurityBridgeType="Auto" />  
    </behavior>  
</endpointBehaviors>  
```      

## See Also  
 [Development Activities](../../esb-toolkit/development-activities.md)