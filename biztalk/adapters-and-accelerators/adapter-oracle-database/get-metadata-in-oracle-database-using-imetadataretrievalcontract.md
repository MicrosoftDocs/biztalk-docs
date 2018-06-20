---
title: "Get Metadata in Oracle Database Using IMetadataRetrievalContract | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "metadata, retrieving using IMetadataRetrievalContract"
ms.assetid: 7d32694f-4384-4c2f-be72-ac52c7b2e9f5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get Metadata in Oracle Database Using IMetadataRetrievalContract
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes an **IMetadataRetrievalContract**endpoint that you can use to browse and search for Oracle database artifacts and to retrieve metadata for operations in the form of a Web Services Description Language (WSDL) document.  
  
 The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and provides metadata browse, search, and retrieval capabilities. In addition to the **IMetadataRetrievalContract** interface, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes the **MetadataRetrievalClient** class, which implements the interface. You can use either an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with metadata; the methods exposed to browse, search, and retrieve metadata are the same in each case.  
  
 The following sections provide information about how to use the **IMetadataRetrievalContract** interface.  
  
## The IMetadataRetrievalContract Interface  
 The following table provides information about important classes that are used when you work with the **IMetadataRetrievalContract** interface.  
  
|Class or Interface|Description|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract** interface<br /><br /> (Microsoft.ServiceModel.Channels)|Defines the **Browse**, **Search**, and **GetMetadata** methods. You invoke these methods either by using an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with adapter metadata.|  
|**MetadataRetrievalClient** class<br /><br /> (Microsoft.ServiceModel.Channels)|Implements the **IMetadataRetrievalContract** interface. You can create an instance of this class and configure it for your Oracle database by providing an **OracleDBBinding** and an **EndpointAddress**. Then you can invoke its methods to work with metadata.|  
|**MetadataRetrievalNode** class<br /><br /> (Microsoft.ServiceModel.Channels)|Represents a metadata node on the adapter. The **Browse** and **Search** methods return nodes of this type, and the **GetMetadata** method takes nodes of this type as a parameter.|  
|**ServiceDescription** class<br /><br /> (System.Web.Services.Description)|Provides a means of creating and formatting a valid WSDL document file. The **GetMetadata** method returns a **ServiceDescription** object.|  
  
 
### Metadata Node IDs  
 The adapter organizes its metadata as a hierarchical tree of nodes. Within this tree structure there are two types of metadata nodes:  
  
- **Operation nodes** represent operations that the adapter surfaces on Oracle database artifacts. Operation nodes are the leaves of the tree.  
  
- **Category nodes** represent Oracle database artifacts and groupings of Oracle database artifacts that do not directly correspond to an operation on the adapter. Category nodes are the branches of the tree; they contain other category nodes and/or operation nodes. For example, Oracle tables and packages are represented as category nodes.  
  
  Each metadata node surfaced by the adapter is identified by a unique node ID. For more information about the metadata node IDs surfaced by the adapter, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md). You use these node IDs to specify target Oracle database artifacts when you use the **IMetadataRetrievalContract** interface to browse, search, and retrieve metadata.  
  
### Binding Properties  
 Whether you use an **IMetadataRetrievalContract** channel or an **IMetadataRetrievalClient** to work with metadata, you must specify an **OracleDBBinding** when you create the instance.  
  
 There are several binding properties that affect how the adapter generates metadata. These properties are:  
  
-   **EnableSafeTyping**  
  
-   **UseSchemaInNamespace**  
  
-   **PollingStatement**  
  
> [!IMPORTANT]
>  If you want to retrieve metadata for the POLLINGSTMT operation you must set the **PollingStatement** binding property.  
  
 You should ensure that these binding properties are set to the values required for your application before you open the metadata retrieval object. For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
### Browsing Metadata Nodes  
 You use the **Browse** method to return all the metadata nodes that are contained in a parent node. The following example browses for the first three schemas on the Oracle database. In this example, **client** is an instance of **MetadataRetrievalClient**.  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
```  
  
> [!IMPORTANT]
>  You can only browse category nodes; you cannot browse operation nodes.  
  
### Searching for Metadata Nodes  
 You use the **Search** method to perform a search for nodes contained by a parent node. The adapter supports wildcard characters in search expressions; for example you can specify the percent (%) wildcard character to match zero or more characters. The following example shows a search for all the tables in the SCOTT schema that contain the string "EMP". In this example, **client** is an instance of **MetadataRetrievalClient**.  
  
```  
// Search for all nodes that contain "EMP" under the SCOTT.Table node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
  
```  
  
> [!IMPORTANT]
>  Searching is only supported on a limited set of nodes. For more information about the nodes on which search is supported and about the wildcard characters supported in search expressions, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
### Retrieving Metadata (WSDL) for Operations  
 You use the **GetMetadata** method to retrieve a service description (WSDL document) for a group of operation nodes. The following example retrieves a service description that contains all of the operations that the adapter surfaces for the SCOTT.EMP table by specifying its node ID. In this example, **client** is an instance of **MetadataRetrievalClient**.  
  
```  
// Get a service description that contains all of the operations   
// surfaced for the SCOTT.EMP table. The IsOperation  
// property is set false because this is a category node.  
nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
nodes[0].IsOperation = false;  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
  
```  
  
> [!IMPORTANT]
>  The **IsOperation** property should be false for category nodes and true for operation nodes.  
  
### Using a MetadataRetrievalClient  
 Creating and using a **MetadataRetrievalClient** is much the same as any other WCF client. You create the client by specifying an endpoint and an instance of **OracleDBBinding**. You can do this either declaratively in configuration or imperatively in your code. You then invoke the methods of the **MetadataRetrievalClient** to browse, search, and retrieve metadata from the adapter.  
  
 The following example shows how to use a **MetadataRetrievalClient** to browse, search, and retrieve metadata from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. The example demonstrates:  
  
-   Browsing the root node of the metadata tree for Oracle Database schemas.  
  
-   Searching for the tables in the SCOTT schema with names that contain the string "EMP".  
  
-   Retrieving metadata for all of the operations supported for the SCOTT.EMP table by passing a category node to the **GetMetadata** method.  
  
-   Retrieving metadata for the POLLINGSTMT operation by passing the POLLINGSTMT operation node to the **GetMetadata** method..  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace OracleMetadataRetrieval  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //write all the nodes returned to the console.  
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
            MetadataRetrievalClient client = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // create a binding and   
                // set the PollingStatement binding property if you want to  
                // return metadata for the POLLINGSTMT operation  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.PollingStatement = "SELECT * FROM EMP";  
  
                // Set PollingId parameter if you want to alter the namespace of the POLLINGSTMT operation  
                EndpointAddress address = new EndpointAddress("oracledb://ADAPTER?PollingId=1");  
  
                client = new MetadataRetrievalClient(binding, address);  
                client.ClientCredentials.UserName.UserName = "SCOTT";  
                client.ClientCredentials.UserName.Password = "TIGER";  
                client.Open();  
  
                // Browse for the first 3 (schema) nodes directly under the root  
                // The parameters are the parent Node ID, the start index, and the maximum number  
                // of nodes to return  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Search for first 3 tables that contain "EMP" in the SCOTT schema  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return  
                nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
                nodeWriter.Write(String.Format("Search results for \"%EMP%\" under {0} node:", "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table"), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // surfaced for the SCOTT.EMP table. The IsOperation property is set false  
                // because this is a category node.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
                nodes[0].IsOperation = false;  
                System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
                description.Write("EmpTableContract.wsdl");  
  
                // Get a WSDL document that specifies a contract that contains the   
                // the POLLINGSTMT operation. The IsOperation property is set true  
                // because this is an operation node.  
                // Note that the operation NodeId is equivalent to the message action.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT";  
                nodes[0].IsOperation = true;  
                description = client.GetMetadata(nodes);  
                description.Write("PollingContract.wsdl");  
  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 The following shows the output of this program on the console. You can see the structure of the metadata retrieval nodes returned by each method. The program also writes two WSDL documents to files.  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTERTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTERTEST  
        Description = Owned By ADAPTERTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTEST  
        Description = Owned By ADAPTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADMIN123  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADMIN123  
        Description = Owned By ADMIN123  
  
Search results for "%EMP%" under http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/AEMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = AEMP  
        Description = Table.AEMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP  
        Description = Table.EMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP1  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP1  
        Description = Table.EMP1  
```  
  
## Using an IMetadataRetrievalContract Channel  
 You can also create an **IMetadataRetrievalContract** channel and then use this channel to browse, search, and retrieve metadata from the adapter. (The method signatures are the same as for the **MetadataRetrievalClient** class.) The following example shows how to do this.  
  
```  
…  
//Create a binding and endpoint address.  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER/");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", int.MaxValue);  
…  
```  
  
## See Also  
 [Get Metadata Programmatically from the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)