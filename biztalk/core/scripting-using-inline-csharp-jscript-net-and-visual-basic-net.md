---
description: "Learn more about: Scripting Using Inline C#, JScript .NET, and Visual Basic .NET"
title: "Scripting Using Inline C#, JScript .NET, and Visual Basic .NET"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Scripting Using Inline C#, JScript .NET, and Visual Basic .NET
Inline scripts are convenient for custom code that you are unlikely to use elsewhere in your application.  
  
 BizTalk saves inline scripts in the Extensible Stylesheet Language Transformations (XSLT) stylesheet defining the map. Because of this, inline scripts may use the same namespaces as any other XSLT stylesheet script. The following table shows the available namespaces.  
  
|Namespace|Description|  
|---------------|-----------------|  
|System|The System class.|  
|System.Collection|The collection classes.|  
|System.Text|The text classes.|  
|System.Text.RegularExpressions|The regular expression classes.|  
|System.Xml|The core XML classes.|  
|System.Xml.Xsl|The XSLT classes.|  
|System.Xml.Xpath|The XPath classes.|  
|Microsoft.VisualBasic|The Visual Basic script classes.|  
  
 For more information about namespaces and data types, search on "XSLT Stylesheet Scripting using \<msxsl:script\>" and on "System.Xml.Xsl.XslCompiledTransform" in the .NET Framework collection.  
  
> [!CAUTION]
>  Avoid using the same method signature more than once. When several Scripting functoids have the same method signature, BizTalk selects the first implementation and disregards the others.  
  
 In addition to being convenient for one-time scripts, inline scripts are also useful for declaring global variables for use among a number of scripts. For example, in a C# inline script, you could place the following line of code outside of any class.  
  
```  
ArrayList statusList = new ArrayList();  
```  
  
 This creates an **ArrayList**, `statusList`, available to all inline scripts in the map.  
  
 For a sample inline script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## See Also  
 [Scripting Functoid](../core/scripting-functoid.md)   
 [Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md)   
 [Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)
