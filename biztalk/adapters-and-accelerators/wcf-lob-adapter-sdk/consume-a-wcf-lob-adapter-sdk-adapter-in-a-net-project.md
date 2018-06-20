---
title: "Consume a WCF LOB Adapter SDK adapter in a .NET project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6934b96d-5704-4f3c-b53f-4e36e352a338
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Consume a WCF LOB Adapter SDK adapter in a .NET project
To consume an adapter built using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must add a service reference to the project. You can do this by:  

- Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], which is installed as part of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  

- Using svcutil.exe (the ServiceModel Metadata Utility), which is installed as part of the Windows SDK.  

## Add a Service Reference using the Add Adapter Service Reference Plug-in  
 The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] can be used to browse and search metadata, and to generate .NET CLR proxy classes using the selected operations and types.  


1. Open your .NET application in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

2. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], right-click the **Project** menu, and then click **Add Adapter Service Reference**.  

   > [!NOTE]
   >  This option does not appear for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects.  

3. In the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] screen, from the **Select a binding** drop-down list, select an adapter binding.  

4. To configure the connection URI for the selected adapter binding and to provide any credentials, URI properties, and binding properties, click **Configure**. Actual requirements vary based on the selected adapter binding.  

5. When you have configured the URI, click **OK**.  

6. Click **Connect**. If the connection URI is valid and client credentials (if any) are accepted, the **Category** pane should be populated with the categories and operations provided by the adapter.  

7. If the adapter supports search, the search field will be active. Otherwise, you can filter by contract type, explore types, and operations by clicking nodes in the **Category** pane.  

8. For advanced proxy generation options, click **Advanced**. Your options include:  


   |                         Option                         |   Equivalent svcutil.exe option    |                                                                     Description                                                                     |
   |--------------------------------------------------------|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
   |           **Generate asynchronous methods**            |               /async               | Generates both synchronous and asynchronous method signatures.<br /><br /> Default (if not selected): generates only synchronous method signatures. |
   |             **Generate message contracts**             |          /messageContract          |                                                          Generates message contract types.                                                          |
   |                **Make types internal**                 |             /internal              |                   Generates classes that are marked as internal.<br /><br /> Default (if not selected): generate public classes.                    |
   |                **Enable data binding**                 |         /enableDataBinding         |              Implements the System.ComponentModel.INotifyPropertyChanged interface on all Data Contract types to enable data binding.               |
   |     **Import non-data types as IXmlSerializable**      |          /importXmlTypes           |                        Configures the Data Contract serializer to import non-Data Contract types as IXmlSerializable types.                         |
   |             **Generate channel interface**             |                                    |                                                          Generates the channel interface.                                                           |
   |             **Mark classes serializable**              |                                    |                                            Selects whether to generate the data types with a serializer.                                            |
   |             **Do not generate app.config**             |             /noConfig              |                                                  Does not generate application configuration file.                                                  |
   |          **Serializer**<br /><br /> **Auto**           |          /serializer:Auto          |                                     Automatically selects the serializer for serialization and deseralization.                                      |
   | **Serializer**<br /><br /> **DataContract Serializer** | /serializer:DataContractSerializer |                         Generates data types that use the Data Contract Serializer for serialization  and de-serialization                          |
   |      **Serializer**<br /><br /> **XmlSerializer**      |     /serializer:XmlSerializer      |                               Generates data types that use the XmlSerializer for serialization and deserialization.                                |


9. To generate the proxy artifacts, click **OK**. The number of artifacts varies based on the contract type.  


   | Contract Type |         Artifact          |                    Description                    |                                                                                                            |
   |---------------|---------------------------|---------------------------------------------------|------------------------------------------------------------------------------------------------------------|
   |   Outbound    |       CLR WCF Proxy       | Contains the contract and service implementation. |                                                                                                            |
   |   Outbound    |                           |                    App.config                     |         Contains the \<endpoint\> and \<bindings\> elements for \<system.ServiceModel\>\<client\>.         |
   |    Inbound    | CLR WCF service interface |              Contains the contract.               |                                                                                                            |
   |    Inbound    |                           |          CLR WCF service implementation           |                            Stub implementation that derives from the contract.                             |
   |    Inbound    |                           |                    App.config                     | Contains the \<endpoint\>, \<bindings\> and \<behaviors\> elements for \<system.ServiceModel\>\<service\>. |


10. You can now use the proxy in your application.  

## Adding a Service Reference by Using svcutil.exe  
 Svcutil.exe is a command-line utility that can be used to retrieve metadata and generate .NET CLR proxy classes, which can then be added to a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project. For more information about svcutil.exe, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx). 

 To generate a proxy class from an adapter hosted in IIS  

1. At the command prompt, enter **svcutil.exe “<http://localhost/adapter/AdapterService.svc?wsdl”> /config:app.config**. Replace the HTTP path with the correct path for your hosted adapter. This creates a .cs file that contains the .NET CLR proxy and output.config which contains the \<bindings\> and client \<endpoint\> for \<system.serviceModel\>.  

   > [!NOTE]
   >  If your adapter contains many operations, you can limit the operations returned by using a query string of ‘op=’ followed by the name of the operation in which you are interested. For example: `svcutil.exe “http://localhost/adapter/AdapterService.svc?wsdl&op=Echo/EchoString&op=Echo/EchoArray”` generates proxy code for only the EchoString and EchoArray operations.  

2. Open your project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

   1.  In **Solution Explorer**, right-click the project, point to **Add**, and then click **New Item**. In the **Add Existing Item** dialog box, select the .cs and app.config files created previously.  Click **Add**.  

   2.  In **Solution Explorer**, right-click **References**, and then click **Add Reference**. On the **.NET** tab, select **System.ServiceModel**, and then click **OK**. You can now use the proxy in your application.  

## See Also  
 [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [Consume an Adapter created using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)