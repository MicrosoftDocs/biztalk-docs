---
title: "Adapter Design Issues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e5568be-a046-40ff-a94a-eda086457564
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Design Issues
Adapter configuration is stored in the Single Sign-On (SSO) database when the user makes configuration changes during design time. At run time the Messaging Engine retrieves the adapter's configuration and delivers it to the adapter. Four types of configuration information are delivered to adapters:  
  
-   Receive handler configuration  
  
-   Receive location (endpoint) configuration  
  
-   Send handler configuration  
  
-   Send location (endpoint) configuration  
  
## Receive and Send Handler Configuration  
 An adapter's handler configuration is delivered to the adapter on its implementation of the optional **IPersistPropertyBag**.**Load** interface. The handler configuration is delivered only once, so if the adapter handler configuration is changed after the BizTalk service has started the adapter is not updated. The common model is for the adapter to treat the handler configuration as the default configuration; endpoint configuration overrides the handler configuration on a per-endpoint basis.  
  
 The following code fragment demonstrates parsing the configuration. The adapter's configuration is in the property passed in to the **Load** call in the string property **AdapterConfig**. This property value contains an XML document representing the adapter's configuration. The adapter needs to load this configuration into a document object model (DOM) or an XML reader and use XPath to retrieve the individual properties.  
  
```  
public class MyAdapter : IBTTransport,   
 IBTTransportConfig,   
 IBTTransportControl,  
 IPersistPropertyBag,   
 IBaseComponent  
{  
...  
// Handler configuration properties...  
private int defaultBatchSize = 0;  
private string defaultHeader;  
  
// IPersistPropertyBag.Load() implementation...  
public void Load(IPropertyBag pb, int pErrorLog)  
{  
// The adapter configuration is in the property  
 // “AdapterConfig” in the form of an Xml blob...  
object obj = null;  
pb.Read("AdapterConfig", out obj, 0);  
  
// Create a DOM and load the Xml blob...  
XmlDocument dom = new XmlDocument();  
string adapterConfig = (string)obj;  
dom.LoadXml(adapterConfig);  
  
// XPath the individual properties...  
XmlNode node =   
 document.SelectSingleNode(“/Config/batchSize”);  
defaultBatchSize = int.Parse(node.InnerText);  
  
node = document.SelectSingleNode(“/Config/header”);  
defaultHeader = node.InnerText;  
}  
}  
```  
  
## Receive Location Configuration  
 Receive location configuration information is delivered to an adapter on its implementation of **IBTTransportConfig**. This interface contains the three methods **AddReceiveEndpoint**, **UpdateEndpointConfig**, and **RemoveReceiveEndpoint**. The Messaging Engine notifies the adapter of which endpoints it needs to listen on to receive messages. When the configuration for an individual endpoint is changed the adapter is notified of the change for that endpoint. This is in contrast to the fact that when handler configuration changes the adapter is not notified. Similarly, the adapter does not need to handle service windows because BizTalk Server adds or removes endpoints as service windows become active or inactive.  
  
### AddReceiveEndpoint  
 When an adapter needs to begin listening on an endpoint, the engine calls **IBTTransportConfig.AddReceiveEndpoint** passing in the receive location's URI, a property bag containing the adapter's configuration for that endpoint, and a second property bag containing BizTalk Server-specific configuration for that endpoint. The adapter needs to write the URI to the message context as the BizTalk Server system property **InboundTransportLocation**.  
  
 Reading the receive location properties from the adapter's property bag is the same as reading the handler configuration as detailed above. The BizTalk Server configuration passed into the adapter contains a single property, **TwoWayReceivePort**, which indicates whether the port is one-way or two-way. The following code fragment illustrates how to evaluate if the receive port is one-way or two-way from the BizTalk Server property bag:  
  
```  
public void AddReceiveEndpoint(  
 string  url,   
 IPropertyBag adapterConfig,   
 IPropertyBag bizTalkConfig )  
{  
...  
  
// The property "TwoWayReceivePort" in the BizTalk Config  
// property bag indicates whether the port is one or two  
 // way...  
  
 // Add receive location to config cache (not shown here)  
  
object obj = null;  
bizTalkConfig.Read("TwoWayReceivePort", out obj, 0);  
  
if ( null != obj )  
this.twoWay = (bool)obj;  
}  
```  
  
### UpdateEndpointConfig  
 When the configuration of an active receive location is changed, the engine uses the **UpdateEndpointConfig** API to notify the adapter that it needs to use a different configuration. All of the configuration is delivered to the adapter, including the BizTalk Server-specific configuration.  
  
### RemoveReceiveEndpoint  
 When a receive location is no longer active, the adapter is notified through **RemoveReceiveEndpoint**. After the adapter returns from **RemoveReceiveEndpoint** it is no longer allowed to use that URI to submit messages into the engine.  
  
## Send Port Configuration  
 The Messaging Engine writes the configuration for the send port to the message context in the adapter’s namespace before delivering the message to the adapter. It is the adapters’ responsibility to read and validate the configuration, which it subsequently uses to control the transmission of the message. For send adapters that support batched sends, messages destined for different send ports may be in the same batch, so the adapter needs to handle these "mixed" batches.  
  
 The following code fragment illustrates how to read the **OutboundTransportLocation** that is the URI for the send port. It also shows how to read the XML blob containing the adapter's configuration and then read the individual properties.  
  
```  
...  
 private static readonly PropertyBase UriProperty =   
 new BTS.OutboundTransportLocation();  
  
 private string propertyNamespace =   
  "http://schemas.mySchemas.com/MyAdapter/myadapter-properties";  
private string uri;  
private string headers;  
private int timeOut = 1000;  
  
private void ReadSendPortConfig(IBaseMessage msg)  
{  
// Read the OutboundTransportLocation,   
 // i.e. the send port uri....  
uri = (string)msg.Context.Read(  
 UriProperty.Name.Name, UriProperty.Name.Namespace);  
  
// Read the adapters configuration Xml blob from   
 // the message...  
XmlDocument locationConfigDom = null;  
object obj = msg.Context.Read(  
 "AdapterConfig", this.propertyNamespace);  
  
// If this is a dynamic send there will not be   
 // any configuration...  
if ( null != obj )  
{  
locationConfigDom = new XmlDocument();  
locationConfigDom.LoadXml((string)obj);  
  
this.headers = Extract(  
 locationConfigDom, "/Config/headers", true);  
  
 this.timeOut = ExtractInt32(  
 locationConfigDom, "/Config/timeOut", true);  
}  
}  
  
 // Helper method to XPath string properties...  
private static string Extract(  
 XmlDocument document, string path, bool required)  
{  
XmlNode node = document.SelectSingleNode(path);  
if (!required && null == node)  
return String.Empty;  
if (null == node)  
throw new ApplicationException(string.Format(  
 "No property was found at {0}", path));  
return node.InnerText;  
}  
  
  // Helper method to XPath int32 properties...  
private static int ExtractInt32(  
 XmlDocument document, string path, bool required)  
{  
string s = Extract(document, path, required);  
return int.Parse(s);  
}   
```  
  
 **Implementation Tip:** Adapters should in general use the **OutboundTransportLocation** message context property to determine the address to send the message to. By doing this the adapter can handle transmissions to both static and dynamic sends consistently. This also simplifies the modification of addresses in production binding files.  
  
## XSD  
 Four XSD files included in the SDK File Adapter sample primarily handle adapter configuration: ReceiveHandler.xsd, ReceiveLocation.xsd, TransmitLocation.xsd, and TransmitHandler.xsd.  
  
 The following topics discuss each of these files and describe how you can modify them.  
  
## In This Section  
  
-   [Validating the Adapter Configuration](../core/validating-the-adapter-configuration.md)  
  
-   [Registering an Adapter](../core/registering-an-adapter.md)  
  
-   [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md)  
  
-   [Supported Adapter XSD Element Types](../core/supported-adapter-xsd-element-types.md)  
  
-   [Adapter XSD Element-Attribute Constructs](../core/adapter-xsd-element-attribute-constructs.md)  
  
-   [Adapter XSD Data Type-Facet Constructs](../core/adapter-xsd-data-type-facet-constructs.md)  
  
-   [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md)