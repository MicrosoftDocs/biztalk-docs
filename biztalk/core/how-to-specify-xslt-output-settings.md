---
title: "How to Specify XSLT Output Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c541432-fd4e-41cc-8bcc-f570ce5df439
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Set map compilation and output settings
Set the map properties in the BizTalk mapper. 

Using these map properties, you can set how maps are compiled, include or exclude an XML declaration, and set the encoding. 

This topic shows you how to set these properties on your map.

## Set the map-level compilation

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you choose the `XslTransform` or the `XslCompiledTransform` class to compile your maps. 

1. Open your map in the Grid view.
2. Right-click anywhere in the mapper grid, and select **Properties**.  
3. Set the **Use XSL Transform** property: 

    | Option | Description |
    | --- | --- |
    | Undefined | The registry flag for the XslTransform setting is used: <ul><li>64-bit host instances: `HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</li><li>32-bit host instances, and Visual Studio’s Test Map functionality: `HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</li></ul> | 
    | True | The map level compilation property is set to `XslTransform` (legacy behavior) | 
    | False | The map level compilation property is set to `XslCompiledTransform` | 

> [!NOTE]
> Starting with BizTalk Server 2013, the mapper compilation behavior was changed from `XslTransform` to `XslCompiledTransform`. The [What the Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) blog post provides a great explanation of the behavior, and its potential impact. 
> 
> Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can choose which class to compile your maps. 
  
## Include or exclude an XML declaration  
You can choose whether an XML declaration is output or not. 

1. Open your map in the Grid view.
2. Right-click anywhere in the mapper grid, and select **Properties**.  
3. In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration. Select **No** not to omit an XML declaration.  

An XML declaration would appear (if you selected **No**) similar to the following.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## Set encoding for output instance data  
Encoding provides the run-time engine with the information it needs to determine which character set to use when creating the output result of a map.  
   
1. Open your map in the Grid view.
2. Right-click anywhere in the mapper grid, and select **Properties**.    
3.  In the drop-down list for the **XSLT Encoding** property, select the character set you want used for the output instance data.  
  
## See Also  
 [Compiling and Testing Maps](../core/compiling-and-testing-maps.md)   
 [Using BizTalk Mapper](../core/using-biztalk-mapper.md)   
 [Valid BizTalk Mapper XSLT Encoding Types](../core/valid-biztalk-mapper-xslt-encoding-types.md)