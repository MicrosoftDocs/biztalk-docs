---
title: "Get Metadata in SAP using IMetadataRetrievalContract | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, search metadata"
  - "searching metadata"
  - "how to, browse metadata"
  - "browsing metadata"
ms.assetid: 0944fc39-9ee5-4702-8b52-e0bc87f202c6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get Metadata in SAP using IMetadataRetrievalContract
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes an **IMetadataRetrievalContract**endpoint that you can use to browse and search for SAP system artifacts and to retrieve metadata in the form of a Web Services Description Language (WSDL) document for operations.  
  
 The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and provides metadata browse, search, and retrieval capabilities. In addition to the **IMetadataRetrievalContract** interface, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes the **MetadataRetrievalClient** class, which implements the interface. You can use either an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with metadata; the methods exposed to browse, search, and retrieve metadata are the same in each case.  
  
 The following sections provide information about how to use the **IMetadataRetrievalContract** interface.  
  
## The IMetadataRetrievalContract Interface  
 The following table provides information about important classes that are used when you work with the **IMetadataRetrievalContract** interface.  
  
|Class or Interface|Description|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract** interface<br /><br /> (Microsoft.ServiceModel.Channels)|Defines the **Browse**, **Search**, and **GetMetadata** methods. You invoke these methods either by using an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with adapter metadata.|  
|**MetadataRetrievalClient** class<br /><br /> (Microsoft.ServiceModel.Channels)|Implements the **IMetadataRetrievalContract** interface. You can create an instance of this class and configure it for your SAP system by providing an **SAPBinding** and an **EndpointAddress**. Then you can invoke its methods to work with metadata.|  
|**MetadataRetrievalNode** class<br /><br /> (Microsoft.ServiceModel.Channels)|Represents a metadata node on the adapter. The **Browse** and **Search** methods return nodes of this type, and the **GetMetadata** method takes nodes of this type as a parameter.|  
|**ServiceDescription** class<br /><br /> (System.Web.Services.Description)|Provides a means of creating and formatting a valid WSDL document file. The **GetMetadata** method returns a **ServiceDescription** object.|  
  
 For more information about the **IMetadataRetrievalContract** interface, the **MetadataRetrievalClient** class, and the **MetadataRetrievalNode** class; see the **Microsoft.ServiceModel.Channels** managed reference at [http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566).  
  
### Metadata Node IDs  
 The adapter organizes its metadata as a hierarchical tree of nodes. Within this tree structure there are two types of metadata nodes:  
  
- **Operation nodes** represent operations that the adapter surfaces on SAP artifacts. Operation nodes are the leaves of the tree.  
  
- **Category nodes** represent SAP artifacts and groupings of SAP artifacts that do not directly correspond to an operation on the adapter. Category nodes are the branches of the tree; they contain other category nodes and/or operation nodes. For example, RFC functional groups or SAP business objects are represented as category nodes.  
  
  Each metadata node surfaced by the adapter is identified by a unique node ID. For more information about the metadata node IDs surfaced by the adapter, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md). You use these node IDs to specify target SAP artifacts when you use the **IMetadataRetrievalContract** interface to browse, search, and retrieve metadata. You can use the constants defined in `Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants` and `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` to help you construct metadata node IDs.  
  
### Binding Properties  
 Whether you use an **IMetadataRetrievalContract** channel or an **IMetadataRetrievalClient** to work with metadata, you must specify an **SAPBinding** when you create the instance.  
  
 There are several binding properties that affect how the adapter generates metadata. These properties are:  
  
- **GenerateFlatfileCompatibleIdocSchema**  
  
- **ReceiveIDocFormat**  
  
- **EnableSafeTyping**  
  
- **FlatFileSegmentIndicator**  
  
  You should ensure that these binding properties are set to the values required for your application before you open the metadata retrieval object. For more information about the SAP adapter binding properties, see [Read about  BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
### Browsing Metadata Nodes  
 You use the **Browse** method to return all the metadata nodes that are contained in a parent node. The following example browses for the first three RFC functional groups on the SAP system. In this example, **client** is an instance of **MetadataRetrievalClient**.  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
```  
  
> [!IMPORTANT]
>  You can only browse category nodes; you cannot browse operation nodes.  
  
### Searching for Metadata Nodes  
 You use the **Search** method to perform a search for nodes contained by a parent node. You can specify the asterisk (\*) wildcard character. This character matches zero or more characters. The following example shows a search for all RFCs that contain the string "BAPI". In this example, **client** is an instance of **MetadataRetrievalClient**.  
  
```  
// Search for all nodes that contain "BAPI" under the RFC node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI*", int.MaxValue);  
```  
  
> [!IMPORTANT]
>  Searching is only supported on a limited set of nodes. For more information about the nodes on which search is supported and about the wildcard character supported in search expressions, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
### Retrieving Metadata (WSDL) for Operations  
 You use the **GetMetadata** method to retrieve a service description (WSDL document) for a group of operation nodes. The following example retrieves a service description for the BAPI_TRANSACTION_COMMIT RFC. In this example, **client** is an instance of **MetadataRetrievalClient**. Note that the node ID for an operation node is equivalent to the message action for that operation.  
  
```  
// Get a WSDL document that specifies a contract that contains the  
// BAPI_TRANSACTION_COMMIT operation.  
MetadataRetrievalNode[] nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
nodes[0].IsOperation = true;  
  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
```  
  
> [!IMPORTANT]
>  You should only specify operation nodes in the **GetMetadata** method.  
  
### Using a MetadataRetrievalClient  
 Creating and using a **MetadataRetrievalClient** is much the same as any other WCF client. You create the client by specifying an endpoint and an instance of **SAPBinding**. You can do this either declaratively in configuration or imperatively in your code. You then invoke the methods of the **MetadataRetrievalClient** to browse, search, and retrieve metadata from the adapter.  
  
 The following example shows how to use a **MetadataRetrievalClient** to browse, search, and retrieve metadata from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace SapMetaDataBrowseClient  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console.  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //Write all the nodes returned to the console.  
            foreach (MetadataRetrievalNode node in nodes)  
            {  
                Console.WriteLine("NodeId = " + node.NodeId);  
                Console.WriteLine("\tDirection   = " + node.Direction.ToString());  
                Console.WriteLine("\tIsOperation = " + node.IsOperation.ToString());  
                Console.WriteLine("\tDisplayName = " + node.DisplayName);  
                Console.WriteLine("\tDescription = " + node.Description);  
            }  
            Console.WriteLine();  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            MetadataRetrievalClient browser = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // Create a binding  
                SAPBinding binding = new SAPBinding();  
  
                EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
                browser = new MetadataRetrievalClient(binding, address);  
                browser.ClientCredentials.UserName.UserName = "YourUserName";  
                browser.ClientCredentials.UserName.Password = "YourPassword";  
                browser.Open();  
  
                // Return the nodes directly under the root.  
                // The parameters are the parent node ID, the start index, and the maximum number  
                // of nodes to return.  
                MetadataRetrievalNode[] nodes = browser.Browse(MetadataRetrievalNode.Root.NodeId, 0, int.MaxValue);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Return first 3 RFC group nodes.  
                nodes = browser.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
                nodeWriter.Write(String.Format("Browse results for the first {1} nodes of {0}:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, nodes.Length), nodes);  
  
                // Search for first 3 nodes that begin with "BAPI_TRANSACTION" under the RFC node.  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return.  
                nodes = browser.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI_TRANSACTION*", 3);  
                nodeWriter.Write(String.Format("Search results for \"*BAPI_TRANSACTION*\" under {0} node:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // found in the search and write it to a file.  
                // You could explicitly specify operations as in the following:  
                //    nodes[0] = new MetadataRetrievalNode();  
                //    nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
                //    nodes[0].IsOperation = true;  
                // Note that the operation NodeId is equivalent to the message action.  
                System.Web.Services.Description.ServiceDescription description = browser.GetMetadata(nodes);  
                description.Write("SampleContract.wsdl");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (browser != null)  
                {  
                    if (browser.State == CommunicationState.Opened)  
                        browser.Close();  
                    else  
                        browser.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 The following shows the output of this program on the console. You can see the structure of the metadata retrieval nodes returned for each method. The program also writes a WSDL document that describes a service contract consisting of the nodes returned by the search to a file. (For most SAP installations, the service description will contain the BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK operations.)  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/BAPISECTION/000001  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = BAPI  
        Description = BAPI  
NodeId = http://Microsoft.LobServices.Sap/2007/03/IDOCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = IDOC  
        Description = IDOC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = RFC  
        Description = RFC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/TRFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = TRFC  
        Description = TRFC  
  
Browse results for the first 3 nodes of http://Microsoft.LobServices.Sap/2007/03  
/RFCSECTION/:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/A  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Asset Accounting  
        Description = Asset Accounting  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/S  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Basis  
        Description = Basis  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/B  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Business Information Warehouse  
        Description = Business Information Warehouse  
  
Search results for "*BAPI_TRANSACTION*" under http://Microsoft.LobServices.Sap/2  
007/03/RFCSECTION/ node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_COMMIT  
        Description = Execute external Commit when using BAPIs  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_ROLLBACK  
        Description = Execute external Rollback when using BAPIs  
  
```  
  
## Using an IMetadataRetrievalContract Channel  
 You can also create an **IMetadataRetrievalContract** channel and then use this channel to browse, search, and retrieve metadata from the adapter. (The method signatures are the same as for the **MetadataRetrievalClient** class.) The following example shows how to do this.  
  
```  
…  
//Create a binding and endpoint address.  
SAPBinding binding = new SAPBinding();  
EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "BAPI_TRANSACTION*", int.MaxValue);  
…  
```  
  
## See Also  
 [Retrieving Metadata Programmatically from SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md)