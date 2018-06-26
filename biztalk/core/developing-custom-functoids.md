---
title: "Developing Custom Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77419e1f-9f01-44ac-bf5b-a393f1d17f61
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing Custom Functoids
Although [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides many functoids to support a range of diverse operations, you will likely encounter a situation that requires a different approach. Custom functoids provide a way for you to extend the range of operations available within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] mapping environment. Each custom functoid is deployed as a .NET assembly using classes derived from **Microsoft.BizTalk.BaseFunctoids**. An assembly can contain more than one custom functoid.  
  
 You should consider using a custom functoid in the following scenarios:  
  
- You have special validation and conversion rules for a character code field using data that is only accessible through a proprietary legacy API.  
  
- You need to encrypt or decrypt fields using custom business logic and key management.  
  
- You need to generate a hash code from part of the message for use in another application.  
  
- Accounting requests that messages transmitted to their department include summary information about total sales by each product type.  
  
- You want to reduce the complexity of a map by combining several related steps, by using a different approach, or by using new class libraries.  
  
- More than one map is using the same script code in a script functoid.  
  
- You need to write to the event log when an operation fails.  
  
  Custom functoids can be integrated into a solution directly by using inline code or indirectly by reference to a method in a class library deployed into the global assembly cache. Both types of integration rely on the **BizTalk.BaseFunctoid** class and follow the same set of general steps:  
  
1. Create a new class library project using the .NET language of your choice.  
  
2. Using the strong-naming utility sn.exe, create a keyfile and assign it to the project.  
  
3. Add a reference to Microsoft.BizTalk.BaseFunctoids.dll. This assembly contains the **BaseFunctoid** base class.  
  
4. Create a resource file and add it to the project. Add string resources for the functoid name, tooltip, and description. Add a 16x16-pixel image resource to represent the functoid on the map designer palette.  
  
5. Implement the functoid class by deriving from **BaseFunctoid**, establishing basic parameters in the constructor, and then writing the functoid method and any supporting methods. The assembly can contain multiple custom functoids.  
  
6. Deploy the assembly and ensure the new functoid is available from the Toolbox palette. See [Adding and Removing Custom Functoids from the Visual Studio Toolbox](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md).  
  
   The following is an illustration for Floor functoid.  
  
```  
/// <summary>  
/// Floor Functoid - finds the floor of input  
/// </summary>  
public class FloorFunctoid : BaseFunctoid  
{  
    public FloorFunctoid()  
        : base()  
    {  
        this.ID = 11001;  
        SetupResourceAssembly("MultipleFunctoids.Resource", Assembly.GetExecutingAssembly());  
  
        SetName("NAME_FLOOR");  
        SetDescription("DESCRIPTION_FLOOR");  
        SetTooltip("DESCRIPTION_FLOOR");  
        SetBitmap("IMAGE_FLOOR");  
  
        SetExternalFunctionName(GetType().Assembly.FullName, " MultipleFunctoids.FloorFunctoid", "MathFloor");  
        this.RequiredGlobalHelperFunctions = InlineGlobalHelperFunction.IsNumeric;  
  
        AddScriptTypeSupport(ScriptType.CSharp);  
        SetMinParams(1);  
        SetMaxParams(1);  
  
        this.Category = FunctoidCategory.Math;  
        this.OutputConnectionType = ConnectionType.AllExceptRecord;  
        AddInputConnectionType(ConnectionType.AllExceptRecord);  
        this.HasSideEffects = false;  
    }  
  
    /// <summary>  
    /// To create the C# function  
    /// </summary>  
    /// <param name="scriptType">Script type</param>  
    /// <param name="numParams">Number of parameters</param>  
    /// <param name="functionNumber">Functoid number</param>  
    /// <returns>C# script</returns>  
    protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
    {  
        if (ScriptType.CSharp == scriptType)  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string MathFloor(string input)\n");  
            builder.Append("{\n");  
            builder.Append("  if(string.IsNullOrEmpty(input))\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("double d = 0.0;\n");  
            builder.Append("if (IsNumeric(input, ref d))\n");  
            builder.Append("    return Math.Floor(d).ToString(System.Globalization.CultureInfo.InvariantCulture);\n");  
            builder.Append("else\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
        else  
        {  
            return string.Empty;  
        }  
    }  
}  
  
```  
  
 While using this sample code as part of your C# project, the “Assembly name” must be set to “MultipleFunctoids”. Your C# project (containing this code) should include a Resource.resx file.  
  
```  
SetName("NAME_FLOOR");  
SetDescription("DESCRIPTION_FLOOR");  
SetTooltip("DESCRIPTION_FLOOR");  
SetBitmap("IMAGE_FLOOR");  
  
```  
  
 In the above code, the values “NAME_FLOOR”, “DESCRIPTION_FLOOR”, and “DESCRIPTION_FLOOR” are the “keys” of resource strings embedded in Resource.resx file. And, “IMAGE_FLOOR” is the name of an image embedded in the Resource.resx file. This image will act as an icon for the functoid.  
  
 If you do not specify proper resource keys, or if you delete the SetName method, then a nameless custom functoid is created, which is not a good practice. Same holds true for SetDescription and SetTooltip methods. Always use these methods properly to avoid any unwanted garbage behavior. However, you may skip the SetBitmap method if you do not have any suitable images to be used as functoid icons. In such a case, a default icon is used by the custom functoid, which is harmless (unless there are multiple icon-less functoids).  
  
 For more information about how to create a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).  
  
> [!IMPORTANT]
>  Certain functoid IDs are reserved by standard/inbuilt Mapper functoids. Usually, the standard Mapper functoids use the IDs from 1 to 10000. While creating custom functoids, do not use the functoid IDs less than 10000.  
  
## In This Section  
 This section contains:  
  
-   [Using BaseFunctoid](../core/using-basefunctoid.md)  
  
-   [Developing a Custom Referenced Functoid](../core/developing-a-custom-referenced-functoid.md)  
  
-   [Developing a Custom Inline Functoid](../core/developing-a-custom-inline-functoid.md)  
  
-   [Developing a Custom Cumulative Functoid](../core/developing-a-custom-cumulative-functoid.md)  
  
-   [Adding and Removing Custom Functoids from the Visual Studio Toolbox](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)  
  
## See Also  
 [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md)