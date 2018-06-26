---
title: "Testing a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 265afd62-3c1d-4b9a-9f51-176b9b079241
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Testing a Map
You can test a map in an EDI project at design time. To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment. This topic describes how to set up and use the **Test Map** feature of the XML Tool extension.  
  
 You test a map by specifying a source document and specifying a folder where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will save a generated instance (with fictitious data). You need to set the delimiters that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to process the source document and generate the destination document according to EDI schemas. This is true for all values of the **TestMap** input property in the map's property pages: **Generate Instance**, **XML**, or **Native**. It is true for **Generate Instance** because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know what delimiters to use to generate the instance. It is true for **XML** or **Native** because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know how to interpret the native flat file or the XML file. You also need to set the delimiters that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use when generating the output file.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To test a map  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], add the map that you want to test to a project, and add the source and destination schemas for that map to the project.  
  
   > [!NOTE]
   >  You do not have to build the project to test the map.  
  
2. Right-click the map and click **Properties**.  
  
3. In the **Properties** window, set **Validate TestMap Input** to **True** if you want to validate the input file against the source schema. Set **Validate TestMap Output** to **True** if you want to validate the output file against the destination schema.  
  
   > [!NOTE]
   >  If you test a map with the **TestMap Input** property set to **Native** and the **Validate TestMap Input** and **Validate TestMap Output** properties set to **False**, validation will still be performed. This occurs because the native-formatted input file will be converted into XML format, and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will validate the XML against the schema. If there are validation issues in the input instance, the validation mechanism will post errors, even though the **Validate TestMap Input** and **Validate TestMap Output** properties are set to **False**.  
  
4. Set **TestMap Input** to **Native** for an input file that has an .edi extension. Set it to **XML** if it has an .xml extension. Set **TestMap Input** to **Generate Instance** to have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generate an input instance, rather than you designating an input instance manually.  
  
5. Set **TestMap Output** to **Native** for an output file that has an .edi extension. Set it to **XML** if it has an .xml extension.  
  
6. For **TestMap Input Instance**, browse to the input instance that you want to be used to test the map, select it, and then **Open**. If you want to leave this property blank, set **TestMap Input** to **Generate Instance**.  
  
   > [!NOTE]
   >  You have to either designate an input instance for **TestMap Input Instance** or set **TestMap Input** to **Generate Instance**. If not, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate an error.  
  
7. For **TestMap Output Instance**, browse to the location you want to save the output instance at, enter a name for the output instance, and then click **Save**.  
  
   > [!NOTE]
   >  If you do not designate an output instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will create an output file, place the output file into a folder, and indicate the file name and path.  
  
8. Right-click the map you are testing, and then click **Test Map**.  
  
9. In the X12 **EDI Instance Properties** dialog box, make sure that all properties are consistent with the settings for the input and output instances.  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the **EDI Instance Properties** dialog box twice during the TestMap process: once for interpreting the input message instance and once for generating the output message instance. However, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may display the dialog box more than just twice and may display the dialog box for non-EDI schema. If so, click **OK** to close the dialog box.  
  
10. Click **OK**.  
  
## See Also  
 [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md)