---
title: "Development best practices using the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ea3a13b-e41f-4920-bf0d-26f7bb145aa3
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Development best practices using the WCF LOB Adapter SDK
You can use the best practices in this topic to improve your applications and adapters.  

## Call Abort Before Close on Channel Exception  
 When you write an application that uses the WCF channel model, you should call `IRequestChannel.Abort` before calling `ChannelFactory.Close`. If you do not, `ChannelFactory.Close` throws an exception.  

 In the following example, channel operations are attempted within a try/catch block. If an exception occurs, the channel is aborted.  

```csharp  
ChannelFactory<IRequestChannel> cf = new  ChannelFactory<IRequestChannel>();  
IRequestChannel channel = null;  
try  
{  
  cf.Open();  
  channel = cf.CreateChannel();  
  channel.Open();  
  channel.Request();// This causes the channel to go into a faulted state.  
  channel.Close();  
}  
catch (Exception e)  
{  
  // Abort the channel if we have one  
  if(channel != null)  
    channel.Abort();  
}  
finally  
{  
  if (cf.State == CommunicationState.Opened)  
  {  
    cf.Close(); // It throws an exception that the channel is in a faulted state.  
  }  
}  
```  

## Implement Both Asynchronous and Synchronous Handlers  
 If possible, implement both asynchronous and synchronous handlers in your adapter. If your adapter only implements synchronous calls, you may run into blocking issues when processing a large volume of messages or when the adapter is used in a multithreaded environment.  

## Use Connection Pooling  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports connection pooling by default. However, it is up to the adapter developer to determine which connection pooling properties to expose as binding properties. The available Connection Pool settings are defined within `Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`.  

 There are no options within the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to easily expose these properties as adapter connection properties. The adapter developer must manually define the properties in the adapter implementation.  

```csharp  
public CustomAdapter(): base()  
{  
   this.Settings.ConnectionPool.EnablePooling = true;  
   this.Settings.ConnectionPool.HandlersShareSameConnection = true;  
   this.Settings.ConnectionPool.MaxConnectionsPerSystem = 50;  
   this.Settings.ConnectionPool.MaxAvailableConnections = 5;  
}  
```  

## Ensure That the Adapter Supports Two-Way Operations  
 If your adapter is called from BizTalk Server, it must support two-way operations, even if the return value is void. This is because BizTalk Server expects a response returned from any outgoing request, and throws an exception if your adapter only implements one-way operations.  

 Here is an example of a request-response contract that returns void.  

```csharp  
[ServiceContract(Namespace=”Http:Microsoft.BizTalk.Samples.WCFAdapterSample”)]  
public interface ICalculator  
{  
   [OperationContract]  
   void Add(double n1, double n2);  
}  
```  

## Implement Tracing  
 During the development cycle, it might not seem important to add tracing to your adapter, since you can step through the code and debug any problems. However, once the adapter is installed in a production environment, you might not be able to use run-time debugging to isolate problems. If you have enabled tracing throughout your adapter, it can be used to isolate where failures are occurring.  

 See [Trace an adapter with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md) for further details.  

## Use URI Properties for Frequently Changed Settings  
 When deciding whether to expose a custom property as a binding or URI property, it is recommended to use a URI property if the value changes often. Binding properties should be reserved for values that rarely change.  

 An example binding property would be a database server name that is used by all connections. An example URI property would be a specific table or stored procedure to be used by that specific connection.  

## Do Not Pass User Name or Password Values in the URI  
 If your adapter requires the caller’s credentials, it is recommended to use the **ClientCredentials** class to retrieve credential values instead of passing client credentials as part of the URI. The **ClientCredentials** class is a standard feature of WCF that is intended for passing credential information from the client to the service in a more secure manner. Passing the user information as part of the URI string may expose the user information while in transit.  

 The recommended methods of passing credentials are shown in the following table.  


|      Method       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Design time    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                When using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you can specify the client credential types that the adapter supports.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|     Run time      | When using a generated .NET CLR proxy, you can programmatically set the client credentials.<br /><br /> `static void Main(string[] args) {    EchoServiceClient client = new EchoServiceClient();    client.ClientCredentials.UserName.UserName = "TestUser";    client.ClientCredentials.UserName.Password = "TestPassword";    string response=client.EchoString("Test String"); }`<br /><br /> Alternatively, if you need to interact with the channel directly, you can use the WCF channel model to specify the client credentials when creating a channel factory.<br /><br /> `EchoAdapterBinding binding = new EchoAdapterBinding(); binding.Count = 3; ClientCredentials clientCredentials = new ClientCredentials(); clientCredentials.UserName.UserName = "TestUser"; clientCredentials.UserName.Password = "TestPassword"; BindingParameterCollection bindingParms = new BindingParameterCollection(); bindingParms.Add(clientCredentials); EndpointAddress address = new EndpointAddress("echo://"); IChannelFactory<IRequestChannel> requestChannelFactory = binding.BuildChannelFactory<IRequestChannel>(bindingParms); requestChannelFactory.Open();` |
| WCF configuration |                                                                                                                                                                                                                                               In the client configuration file, add an \<endpointBehaviors\> element that includes \<clientCredentials\>.<br /><br /> `<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">       <system.serviceModel>           . . . . .           <behaviors>             <endpointBehaviors>               <behavior name="clientEndpointCredential">                 <clientCredentials>                   <windows allowNtlm="false" allowedImpersonationLevel="Delegation" />                    </clientCredentials>               </behavior>             </endpointBehaviors>           </behaviors>       </system.serviceModel>   </configuration>`                                                                                                                                                                                                                                               |
|   Using BizTalk   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 When using the WCF adapter to consume your adapter, you can add the **clientCredentials** behavior extension on the **Behavior** tab. Once this has been added, you can set the desired client credentials in the endpoint behavior.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## Do Not Return Both StrongDataSetType and WeakDataSetType  
 If your adapter returns a `DataSet`, use either `Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A` or `Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`, but do not use both at the same time. The root node name and namespace produced by both types are identical, and cannot exist simultaneously in a WSDL.  

 While `WeakDataSetType` and `StrongDataSetType` both represent a `System.Data.DataSet`, `StrongDataSetType` is easier to use in .NET applications, since the proxy generated appears as `System.Data.Dataset`. The proxy generated by `WeakDataSetType` is `XmlElement[]`, which is more difficult to use in a .NET application.  BizTalk Server cannot consume the schema returned from `StrongDataSet`, but is able to consume `WeakDataSetType`.  

> [!NOTE]
>  `StrongDataSetType` and `WeakDataSetType` only control how the client application interprets the XML messages passed by the adapter. The XML message is the same regardless of which type is specified.  

> [!NOTE]
>  When returning `StrongDataSetType`, you must set `Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A` to `false`. When set to `true`, the default, `XmlSchemaSet::Compile` is called within the adapter to ensure there are no errors in the WSDL, however the schema produced by `StrongDataSetType` generates an exception in `XmlSchemaSet`.  
>   
>  Setting `CompileWsdl` to `false` bypasses WSDL schema validation within the adapter and validation occurs during proxy generation.  Utilities such as svcutil.exe are able to generate a proxy for both `StrongDataSetType` and `WeakDataSetType`.  

 To work with both BizTalk and .NET environments, consider implementing a binding property that allows switching between the two return types as dictated by the environment.  

```csharp  
internal static QualifiedType GetDataSetQualifiedType(MyAdapterBindingProperties bindingProperties)  
{  
   if (bindingProperties.EnableBizTalkCompatibility)  
      return QualifiedType.WeakDataSetType;  
   else  
      return QualifiedType.StrongDataSetType;  
}  
```  

## Create Meaningful XSD Schema Names in BizTalk Server  
 When using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] design-time tool, the name of the XSD schema generated in your BizTalk project is created using the `DefaultXsdFileNamePrefix` property, the `fileNameHint` annotation in the WSDL and, if required, a unique integer value.  

 For example, if `DefaultXsdFileNamePrefix` is set to “MyAdapter” and the `fileNameHint` annotation is set to “Stream”, the XSD schema created is named MyAdapterStream.xsd.  

```  
<xs:schema elementFormDefault='qualified' targetNamespace='http://schemas.microsoft.com/Message' xmlns:xs='http://www.w3.org/2001/XMLSchema' xmlns:tns='http://schemas.microsoft.com/Message'>  
<xs:annotation>  
<xs:appinfo>  
<fileNameHint xmlns='http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd'>Stream</fileNameHint>  
</xs:appinfo>  
</xs:annotation>  
<xs:simpleType name='StreamBody'>  
<xs:restriction base='xs:base64Binary' />  
</xs:simpleType>  
</xs:schema>  

```  

> [!NOTE]
>  The default value of `DefaultXsdFileNamePrefix` is the name of your binding. To specify a different value, override `DefaultXsdFileNamePrefix` in your Adapter class that is derived from `Microsoft.ServiceModel.Channels.Common.AdapterBinding`.  

 There are two possible methods to add the `fileNameHint` annotation to the schema: override the Export…Schema methods on OperationMetadata\TypeMetadata or override the IWsdlRetrieval implementation of the adapter. For either method, you can call the base implementation and then add the annotation to the schemas in the schema collection.  

> [!NOTE]
>  When overriding the Export…Schema methods, there may be multiple operation/type definitions in the same schema; the adapter should make sure that multiple occurrences of the `fileNameHints` annotation in the same schema do not conflict. The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] uses the first occurrence of `fileNameHint` if it occurs multiple times within a schema.  

 In the following example, IWsdlRetrieval is used to add the `fileNameHint` annotation to the WSDL.  

```csharp  
sealed class MyAdapterWsdlRetrieval : IWsdlRetrieval  
{  
   IWsdlRetrieval mBaseWsdlRetrieval;  
   public MyAdapterWsdlRetrieval(IWsdlRetrieval baseWsdlRetrieval)  
   {  
      mBaseWsdlRetrieval = baseWsdlRetrieval;  
   }  

   ServiceDescription IWsdlRetrieval.GetWsdl(Microsoft.ServiceModel.Channels.MetadataRetrievalNode[] nodes, Uri uri, TimeSpan timeout)  
   {  
      ServiceDescription baseDesc = mBaseWsdlRetrieval.GetWsdl(nodes, uri, timeout);  
      foreach (XmlSchema schema in baseDesc.Types.Schemas)  
      {  
         CreateFileNameHint(schema);  
      }  
      return baseDesc;  
   }  

   void CreateFileNameHint(XmlSchema schema)  
   {  
      string targetNamespace = schema.TargetNamespace;  
      if (string.IsNullOrEmpty(targetNamespace))  
         return;  
      string fileNameHint = null;  
      //determine the filename based on namespace  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadaptpter/HelloWorld"))  
      {  
         fileNameHint = "HelloWorld";  
      }  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadapter/Hello"))  
      {  
         fileNameHint = "Hello";  
      }  
      //create the annotation and populate it with fileNameHint  
      XmlSchemaAnnotation annotation = new XmlSchemaAnnotation();  
      XmlSchemaAppInfo appInfo = new XmlSchemaAppInfo();  
      XmlDocument doc = new XmlDocument();  
      XmlNode[] fileNameHintNodes = new XmlNode[1];  
      fileNameHintNodes[0] = doc.CreateElement(null, "fileNameHint", "http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd");  
      fileNameHintNodes[0].AppendChild(doc.CreateTextNode(fileNameHint));  
      appInfo.Markup = fileNameHintNodes;  
      annotation.Items.Add(appInfo);  
      schema.Items.Insert(0, annotation);  
   }  
```  

## Do Not Modify AdapterEnvironmentSettings During Processing  
 The adapter should only set the **AdapterEnvironmentSettings**, **ConnectionPoolManager**, **ConnectionPool**, and **CommonCacheSize** during adapter initialization and should not attempt to modify the values for a running instance.  

 If these settings are modified on a currently running adapter instance, this may result in new connections overwriting configuration settings for currently executing connections.  

## See Also  
 [Development best practices using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)