---
title: "How to Configure a SOAP Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [SOAP adapters], virtual directories"
  - "SOAP adapters, code samples"
  - "configuring [SOAP adapters], receive locations"
  - "virtual directories, SOAP adapters"
  - "SOAP adapters, receive locations"
  - "code samples, SOAP adapters"
  - "configuring [SOAP adapters], code samples"
  - "SOAP adapters, virtual directories"
  - "receive locations, SOAP adapters"
ms.assetid: 7e348409-9181-47e4-b3c0-c73eb2acffa3
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a SOAP Receive Location
You can configure a SOAP receive location either programmatically or by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

 **How to Configure a SOAP Receive Location Programmatically**  

 The BizTalk Explorer object model enables you to create and configure receive locations programmatically. The BizTalk Explorer object model exposes the**IReceiveLocation** receive location configuration interface that has a **TransportTypeData** read/write property. This property accepts a SOAP receive location configuration property bag in the form of a name-value pair of XML strings. To set this property in the BizTalk Explorer object model, you must set the **InboundTransportLocation** property of the **IReceiveLocation** interface.  

 The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set. If it is not set, the SOAP adapter uses the default values for the SOAP receive location configuration as indicated in the following table.  

 The following table lists the configuration properties that you can set in the BizTalk Explorer object model for the SOAP receive location.  

|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**URI**|String|Virtual directory containing the Web service on the deployment server.|  
|**AddressableURI**|String|Public address field containing the entire, callable URL.<br /><br /> Default value: Blank|  
|**UseSSO**|Boolean|Specifies whether the SOAP adapter issues the Single Sign-On ticket to the messages that arrive on this receive location.<br /><br /> Default value: False|  

 Use the following format to set the properties:  

```  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
```  

 The **URI** and **AddressableURI** properties are set using the **Address** and **PublicAddress** properties of the receive location object.  

 The following code fragment illustrates creating a SOAP receive location:  

```  
// Use BizTalk Explorer object model to create new SOAP receive location.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  

// Add a new Request-Response port  
ReceivePort receivePort = explorer.AddNewReceivePort(true);  
receivePort.Name = "SampleReceivePort";  
receivePort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  

// Add primary SOAP receive location  
ReceiveLocation receiveLocation = receivePort.AddNewReceiveLocation();  
receiveLocation.Name = "SampleReceiveLocation";  
receiveLocation.Address = "/PurchaseOrder/POOrchestration.asmx";  
receiveLocation.TransportType = explorer.ProtocolTypes["SOAP"];  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
receiveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
foreach (ReceiveHandler receiveHandler in explorer.ReceiveHandlers)  
{  
if (receiveHandler.TransportType.Name == receiveLocation.TransportType.Name)  
{  
receiveLocation.ReceiveHandler = receiveHandler;   
}  
}  

// Save  
explorer.SaveChanges();   
```  

 **How to Configure a SOAP Receive Location with the BizTalk Server Administration Console**  

 You can set SOAP receive location adapter variables in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. If properties are not set in the receive location, the default receive handler values set in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console are used.  

> [!NOTE]
>  Before completing the following procedures you must have already added a receive port. For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  

### To configure variables for a SOAP receive location  

1. In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application you want to create a receive location in.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, in the left pane, click the **Receive Port** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  

3. In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.  

4. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **SOAP** from the drop-down list, and then click **Configure**.  

5. In the **SOAP Transport Properties** dialog box, do the following:  


   |                     Use this                      |                                                                                                                                                                                                                                                                                                              To do this                                                                                                                                                                                                                                                                                                               |
   |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Virtual directory plus Web Service .asmx file** |                                                                                                                 Indicate the .asmx file created by the BizTalk Web Services Publishing Wizard.<br /><br /> The format of this message is similar to the following:<br /><br /> /PurchaseOrder/POOrchestration.asmx<br /><br /> Where the full location of the .asmx file is http://localhost/PurchaseOrder/POOrchestration.asmx. **Note:**  The URI for a send port or receive location cannot exceed 256 characters.                                                                                                                 |
   |                **Public address**                 | Specify the fully qualified URI for this receive location. The value for this property is a combination of the server name and the virtual directory. The specified URI should designate the public Web site URL for trading partners to connect to when sending messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].<br /><br /> This information is optional and is not used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This parameter is available to allow administrators to document the public URL that the receive location is tied to. |
   |              **Use Single Sign-On**               |                                                                                                                                                                                                 Indicate that the SOAP adapter uses Enterprise Single Sign-On. **Note:**  The BizTalk Web Services Publishing Wizard allows you to use SharePoint Portal Server Single Sign-On; this property only enables Enterprise Single Sign-On.                                                                                                                                                                                                 |


6. Click **OK**.  

7. In the **Receive Location Properties** dialog box, enter the appropriate values to complete the configuration of the receive location, and then click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

   The security settings used by the SOAP receive location are set in IIS. By default, the SOAP receive location is not set to use anonymous authentication.  

   While the SOAP client calls the Web service, the SOAP adapter authenticates the SOAP client by using either Anonymous, Basic, Digest, or Windows Integrated authentication. If the user is verified, the user context is passed to the receive handler.  

> [!NOTE]
>  Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid. You can have only one isolated receiver per process.  

### To update a virtual directory to use ASP.NET 4.0  

1.  Launch the Internet Information Services (IIS) Manager. Click **Start**, click **All Programs**, and click **Internet Information Services (IIS) Manager**.  

2.  If you need to connect to a remote IIS server, right click the **Internet Information Services** node and then click **Connect**.  

3.  Type the computer name for the remote IIS server and credentials if necessary.  

4.  Expand the server name that houses the Web site or virtual directory to be updated.  

5.  Expand **Sites**.  

6.  Expand **Default Web Site**.  

7.  Expand the Default Web site to view the virtual directories under the Web site.  

8.  Right-click the virtual directory that you want to update to use ASP.NET 4.0, click **Manage Application**, and then click **Advanced Settings**. The **Application Pool** field displays the application pool set for the selected virtual directory. Click **OK**.  

9. In the Internet Information Services (IIS) Manager window, click **Application Pools**. The details pane displays a list of application pools on the server.  

10. Right-click the application pool set in step 8, and then click **Basic Settings**.  

11. In the **Edit Application Pool** dialog box, change the following:  

    -   **.NET Framework version** to **4.0**  

    -   **Managed pipeline mode** to **Classic**  

12. Click **OK** to apply the changes.  

## See Also  
 [Consuming Web Services](../core/consuming-web-services.md)