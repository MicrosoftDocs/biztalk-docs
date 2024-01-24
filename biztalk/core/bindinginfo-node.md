---
description: "Learn more about: BindingInfo Node"
title: "BindingInfo Node"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# BindingInfo Node
The **BindingInfo** node of a binding file is the root node of a binding file and contains information that applies to all of the entries in the binding file as well as information about the BizTalk Server that the binding file was exported from.  
  
## Nodes in the BindingInfo node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Assembly|Attribute|xs:string|Specifies information for the Microsoft.BizTalk.Deployment dll used when creating the binding file. Includes comma separated Version, Culture, and PublicKeyToken attributes for this assembly.|Required|Default value: **"Microsoft.BizTalk.Deployment, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"**|  
|Version|Attribute|xs:string|Specifies the version of BizTalk Server that the binding file was generated on.|Required|Default value: **3.5.1.0**|  
|BindingStatus|Attribute|BindingState (SimpleType)|Specifies the binding status of the artifacts exported with the binding file.|Required|Default value: None<br /><br /> Valid values:<br /><br /> -   Unknown<br />-   NoBindings<br />-   Unbound<br />-   PartiallyBound<br />-   FullyBound|  
|BoundEndpoints|Attribute|xs:int|Specifies the number of bound endpoints in the binding file.|Required|Default value: **0**|  
|TotalEndpoints|Attribute|xs:int|Specifies the total number of endpoints in the binding file.|Required|Default value: **0**|  
|Description|Element|xs:string|Specifies a text description of the BindingInfo section of the binding file.|Not required|Default value: empty|  
|Timestamp|Element|xs:dateTime|Specifies when the binding file was exported.|Required|Default value: Time on the BizTalk server when the binding file was exported.|  
|[ModuleRefCollection Node](../core/modulerefcollection-node.md)|Record|ArrayOfModuleRef (ComplexType)|Container node for the .NET assemblies exported with the binding file.|Not required|Default value: none|  
|[SendPortCollection Node](../core/sendportcollection-node.md)|Record|ArrayOfSendPort (ComplexType)|Container node for the send ports exported with the binding file.|Not required|Default value: none|  
|[DistributionListCollection Node](../core/distributionlistcollection-node.md)|Record|ArrayOfDistributionList (ComplexType)|Container node for the distribution lists exported with the binding file.|Not required|Default value: none|  
|[ReceivePortCollection Node](../core/receiveportcollection-node.md)|Record|ArrayOfReceivePort (ComplexType)|Container node for the receive ports exported with the binding file.|Not required|Default value: none|  
  
 The following code shows the format of the XML used in the BindingInfo node of a binding file:  
  
```  
<BindingInfo xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
Assembly="Microsoft.BizTalk.Deployment, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
Version="3.5.1.0" BindingStatus="FullyBound"   
BoundEndpoints="12"   
TotalEndpoints="12">  
<Description/>  
<Timestamp>2005-08-23T16:27:40.5948205-07:00</Timestamp>  
```  
  
## See Also  
 [Customizing Binding Files](../core/customizing-binding-files.md)
