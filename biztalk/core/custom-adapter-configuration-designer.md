---
title: "Custom Adapter Configuration Designer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9b231c3-3948-4db8-b4f0-d9c21c31b168
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Adapter Configuration Designer
You need to build the custom designers into a .NET class library. You may incorporate them into the DLL for the adapter or build a separate DLL. After you build a designer assembly, you must reference it through decorations, just like a description or a category. The reference includes a specification of the assembly and a fully qualified class name to use.  
  
 These decorations support two ways of referencing the specific custom designer: as a global assembly in the global assembly cache or as an external assembly located on the disk.  
  
> [!NOTE]
>  There are two possible design-time assembly paths: You can specify the absolute path to the type editors and converters used in the configuration XSD in the XSD itself (relative path is not supported), or you can store the type editors and converters in the global assembly cache and not need an absolute path.  
  
## Global Assembly Cache Designer Use  
 The global assembly cache stores assemblies by assembly name, public key, version, and culture. Because of this, it is recommended that you:  
  
1. Generate a public key file and add this file to the AssemblyInfo.cs file.  
  
2. Specify a specific version in the AssemblyInfo.cs file.  
  
   You can either drag the assembly into the global assembly cache or use GACUTIL to add it to the global assembly cache.  
  
   To use this designer, specify the fully qualified class name, a comma, and the global assembly cache assembly entry (assembly name, version, culture, and public key token) as the value of the decoration. Use \<editor\> decorations for **UITypeEditor** implementations and \<converter\> decorations for **TypeConverter** implementations.  
  
   The following code shows how to initialize the custom designers in an XSD file:  
  
```  
<xs:element name="Global" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>GAC Designer Component</baf:category>  
            <baf:editor>AdapterManagement.ComponentModel. PasswordUITypeEditor, AdapterManagement, Version=1.0.1.0, Culture=neutral, PublicKeyToken=f0db50abb0615c18</baf:editor>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
      </xs:sequence>  
```  
  
## External Assembly Installation and Use  
 For external assemblies, the decoration contains an optional attribute assembly that specifies the full path and name of the assembly containing the desired designer.  
  
 The following code shows how to initialize the custom designers contained in external assemblies:  
  
```  
<xs:element name="External" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>External Designer Component</baf:category>  
            <baf:converter assembly="C:\source\private\Adapter\Framework\Designer\bin\Debug\Designer.External.dll">Designer.External.DesignerTypeConverter</baf:converter>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
```  
  
## See Also  
 [Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [Custom Type Converter for Adapter Configuration](../core/custom-type-converter-for-adapter-configuration.md)   
 [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md)