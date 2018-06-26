---
title: "How to Add Scripting Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.functiod.script"
ms.assetid: eb96814a-b3fb-48f6-a947-ab595a270faa
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Scripting Functoids to a Map
The **Scripting** functoid enables you to use custom script or code at run time to perform functions otherwise not available. For example, you can call a COM object at run time by using the **Scripting** functoid and writing your own custom script.  
  
 For conceptual information about the **Scripting** functoid, see [Scripting Functoid](../core/scripting-functoid.md).  
  
### To add the Scripting functoid to a map and configure it  
  
1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.  
  
    The list of advanced functoids in the chosen category appears.  
  
2. Drag the **Scripting** functoid ![](../core/media/bts-tls-scripting.gif "bts_tls_scripting") from the Toolbox to the appropriate location on a grid page.  
  
   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first.  
  
   > [!NOTE]
   >  If you are constructing a map using more than one functoid together, you need to consider their relative left-to-right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  
  
3. Select the **Scripting** functoid that you just added to the displayed grid page.  
  
4. In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, click the ellipsis (**...**) button associated with the **Script** property.  
  
   > [!NOTE]
   >  Alternatively, you can right-click the functoid, and then click **Configure Functoid Script** in the context menu. The **Configure Scripting Functoid** dialog box appears with the **Script Functoid Configuration** tab selected.  
  
5. In the **Configure Scripting Functoid** dialog box, in the **Select script type** drop-down list, select the type of your script.  
  
   > [!NOTE]
   >  Depending on your selection of script type, different subsets of the remaining dialog box fields will be enabled and disabled.  
  
6. If you selected **External Assembly** as the script type, use the **Script assembly**, **Script class**, and **Script method** drop-down lists, in that order, to select the assembly, class, and method, respectively, to associate with this **Scripting** functoid.  
  
   > [!WARNING]
   >  The code in the external assembly must be thread-safe. Under stress conditions, multiple instances of a map may be running concurrently.  
  
   > [!NOTE]
   >  After you have selected an assembly, the **Script class** drop-down list will be populated with the classes in that assembly. Likewise, after you have selected a class, the **Script method** drop-down list will be populated with the methods in that class.  
  
   > [!NOTE]
   >  The **Inline script** text box is disabled when you select **External Assembly** as the script type.  
  
    If you selected something other than **External Assembly** as the script type (one of the inline choices), use the **Inline script** text box to enter your script in the language you selected.  
  
   > [!NOTE]
   >  The inline language choices for the **Scripting** functoid include C# .NET, JScript.NET, Visual Basic .NET, XSLT, and XSLT Call Template.  
  
    Scripting using C# does not allow "using" statements. If the script needs to use any special .Net classes, then the corresponding assemblies and their dependent assemblies should be added to "References" in the BizTalk project, and the script code should use fully qualified names. If you write a script to perform culture-sensitive lowercase conversion, the corresponding code fragment should be written as below. Similar limitations apply to all supported scripting languages.  
  
   ```  
   string x = y.ToLower(System.Globalization.CultureInfo.CurrentCulture);  
   ```  
  
    In the script, to use classes from any assembly, ensure you add the corresponding assembly and its dependent assemblies to “References” in the BizTalk project containing your map.  
  
   > [!NOTE]
   >  You can create your custom script directly in the **Inline script** text box, or you can create your script elsewhere, and paste it into the **Inline script** text box.  
  
   > [!NOTE]
   >  The **Script assembly**, **Script class**, and **Script method** drop-down lists are disabled when you select one of the inline choices (something other than **External Assembly**) as the script type.  
  
   > [!IMPORTANT]
   >  If you create a script containing multiple functions, the first function will be treated as the main or primary function; other functions are only called if they are called in the execution of the primary function.  
  
    Click **OK**.  
  
7. If your script or the associated method in an external assembly requires input parameters, create the appropriate number and type of input links as you would for a basic functoid.  
  
8. In most circumstances, your **Scripting** functoid will produce an output value used to populate a field in the destination schema, or as input to another functoid, in much the same way that basic functoids do.  
  
## See Also  
 [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)