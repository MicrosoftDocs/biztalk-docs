---
title: "Implementing Character Encoding in a Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], examples"
  - "pipeline components [custom], code samples"
  - "pipeline components [custom], encoding"
ms.assetid: 862b56da-ec14-41f9-b63c-42d81124e167
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing Character Encoding in a Pipeline Component
To support custom character encoding, you must implement a custom encoding class by deriving from the Microsoft .NET Framework **Encoding** class, then create a custom flat file pipeline component by inheriting from the standard Flat File Disassembler or Flat File Assembler component. You can supply a new encoding instance to the parsing engine by overriding the protected virtual method **FFDasmComp.GetDataReader** as shown in the following example.  
  
```  
/// <summary>  
/// Gets a data reader instance  
/// </summary>  
/// <param name="dataStream">Data stream</param>  
/// <param name="dataEncoding">Data encoding</param>  
/// <param name="detectEncodingFromByteOrderMarks">Detect encoding from a byte order mark</param>  
/// <returns>IDataReader instance</returns>  
      protected override IDataReader GetDataReader(Stream dataStream, Encoding dataEncoding, bool detectEncodingFromByteOrderMarks)  
      {  
         // Delegate call to the base implementation passing fixed UTF-7 encoding  
         return base.GetDataReader(dataStream, new CustomEncoding(), false);  
      }  
```  
  
## Using predefined encoding classes  
 The following encoding types are predefined by the Microsoft .NET Framework and can be used to construct the parser:  
  
-   ASCII  
  
-   UTF7  
  
-   UTF8  
  
-   Unicode (UTF16)  
  
```  
XmlReader xr = docspec.Parse(new DataReader(System.Text.Encoding.UTF8));  
```  
  
## Using supported code pages  
 Use the following code to support Shift-JIS (codepage 932).  
  

```  
XmlReader xr = docspec.Parse(new DataReader(System.Text.Encoding.GetEncoding(932)));  
```  
  
## Using a private encoding class  
 You can create your own encoding class that derives from the **System.Text.Encoding** abstract class and perform your own encoding and decoding.  
  
```  
class MyEncoding : System.Text.Encoding  
{  
   // overriding methods omitted  
}  
  
XmlReader xr = docspec.Parser(new DataReader(new MyEncoding()));  
```  
  
## Using a private DataReader class  

 You can create your own [DataReader](https://msdn.microsoft.com/library/microsoft.biztalk.parsingengine.datareader.aspx) class that implements the `IDataReader` interface and performs reading without creating any encoding classes.  
  
```  
class MyDataReader : IDataReader  
{  
   // Implement data reader functions  
   // ...  
}  
  
XmlReader xr = docspec.Parse(new MyDataReader());  
```  
  
## See Also  
 [Using the Parsing and Serializing Engines](../core/using-the-parsing-and-serializing-engines.md)