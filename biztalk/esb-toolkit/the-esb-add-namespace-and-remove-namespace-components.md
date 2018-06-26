---
title: "The ESB Add Namespace and Remove Namespace Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21df1b21-b73c-4e31-a234-49a1a6b53cc7
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The ESB Add Namespace and Remove Namespace Components
Many companies were early adopters of XML technologies at the time when standards were still emerging and document sharing was uncommon. Therefore, they did not strictly enforce the requirements for including unique root namespaces, which is usually the case today.  
  
 However, Microsoft BizTalk Server performs document identification based on a combination of the root node namespace and the root node name, so documents that have no namespace for the root node are difficult to positively identify if several different document types use the same root node name.  
  
 The Add Namespace and Remove Namespace components solve this problem by making it possible to add namespaces to documents when they are received and to remove the namespace from the documents before they are delivered. Therefore, documents can reside in the default namespace (or in a namespace common to several different document types) when they are sent and received but reside in a transient unique root namespace during processing within the ESB and BizTalk.  
  
 The components are also useful when integrating legacy systems that use a Document Type Definition (DTD) instead of an XML Schema definition or that use legacy XML parsers that cannot create documents that contain a root namespace.  
  
## Installation  
 Installing the ESB Core automatically installs the **Add Namespace** and **Remove Namespace** components in the BizTalk Server Pipeline Components folder.  
  
## How It Works  
 The Add Namespace component adds a specified namespace to an XML document. The component can add only a single namespace to a document. Using the Add Namespace component on a document that already has a root node namespace is not a supported scenario because a single unique namespace is all that is required.  
  
 The components are not namespace-aware and do not persist any of the namespace values. However, the Add Namespace component compares the requested namespace in the existing namespace of the message and simply returns the original message to the pipeline if they match.  
  
 Developers include the Add Namespace component in a receive pipeline or a send pipeline and set the appropriate properties. The following validation is performed at run time:  
  
- The **XPaths** property or the **NamespaceBase** property must contain a value.  
  
- The **Separator** property can contain only valid characters (such as **/** or **\\**) or an empty string.  
  
- The **NamespacePrefix** property value cannot be one of the reserved values (**ns0** to **ns6**) and must be alpha numeric.  
  
  Any variation from these rules causes the component to throw an exception at run time, suspend the message (marked as **Suspended – Resumable**), and write an entry in Windows Application Event Log.  
  
  The Remove Namespace component removes all root namespaces from an XML document. The number of namespaces that the component can remove from a single document is constrained by the physical memory available to hold the current node during processing. However, the component uses standard BizTalk Server 2009 pipeline message streaming processes and loads only the current node in the document into memory instead of loading the entire document.  
  
  The Remove Namespace component also re-encodes the document to the specified encoding (**ascii, unicode/utf16,** or **utf8**) and can remove the Byte Order Mark (BOM) from the beginning of the stream, if required.  
  
## Using the Add Namespace and Remove Namespace Components  
 Developers might use the Add Namespace component in any of the following circumstances:  
  
- The inbound message has no root namespace.  
  
- The inbound message uses element data or attribute data to describe the message type.  
  
- The data describing the message type is consistent and available using XPath queries.  
  
  The Add Namespace and Remove Namespace components can reside in any stage of a receive pipeline or a send pipeline. You can chain instances of the component if required, such as if you are using the Remove Namespace component followed by the Add Namespace component to change the root namespace of a document.  
  
  If you have multiple receive locations that require the use of these components, you can create a single pipeline and use the BizTalk Server "per instance" component configuration to set the component properties for each instance of the send or receive pipeline. Using BizTalk Server 2009, you can set properties on a per-instance basis for pipelines, which means that you can reuse a single pipeline across multiple receive locations and perhaps have different component properties for each instance. This is a run-time setting that allows administrators to make the change using the BizTalk Server Administration Console without requiring changes to the code or redeployment.  
  
## Component Properties  
 The Add Namespace component exposes five public properties:  
  
-   **NamespacePrefix**. This is the prefix of the namespace, inserted between the **xmlns:** part and the following equals sign ( = ). To avoid conflicts with standard BizTalk Schema namespace prefixes, avoid using the values **ns0** through **ns9**.  
  
-   **NamespaceBase**. This is the static section of the namespace that will prefix the result generated by the values in the **Separator** and **XPaths** properties.  
  
-   **ExtractionNodeXPath**. This is an XPath statement that resolves to a single element in the document that contains the element or attribute values you want to use for the generated parts of the namespace.  
  
-   **XPaths**. This is a pipe (**&#124;** ) delimited list of XPath queries used to extract each of the components that will combine to form the namespace.  
  
-   **Separator**. This is the separator to use between the namespace segments. The most common value is a forward slash (**/** ), but it can be an empty string, if required.  
  
> [!NOTE]
>  All XML nodes, such as element and attribute names, are case sensitive.  
  
 The Remove Namespace component exposes two public properties:  
  
- **Encoding**. This is the encoding for the output message, one of the following values: **ascii, unicode/utf16,** or **utf8**.  
  
- **RemoveByteOrderMark**. This is a Boolean property that indicates whether the component should remove the byte order mark (usually **0xEFBB, 0xBFFFFE,** or **0xFEFF**) from the beginning of the XML document stream.  
  
  For an example of how to use these components, see [Installing and Running the Namespace Component Sample](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).