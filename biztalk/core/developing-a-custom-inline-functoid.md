---
title: "Developing a Custom Inline Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4533f09f-b62d-4b09-b7de-44541c6cf053
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing a Custom Inline Functoid
Custom inline functoids provide functionality by copying implementation code directly into a map and not by referencing an assembly, class, and method name like a custom referenced functoid.  
  
## Building Inline Script  
 There are two ways to provide script for inclusion into the map. Choose from the following methods, based on whether your custom functoid supports a variable number of parameters:  
  
- Override **GetInlineScriptBuffer** when your custom functoid accepts a variable number of input parameters and you have set the **HasVariableInputs** property to `true`. For example, use this method if you want to concatenate a variable number of strings or find the largest value in a set of values.  
  
- Use **SetScriptBuffer** when you do not need to support a variable number of input parameters. You can still use optional parameters, but the total number of parameters is fixed.  
  
  These two methods require different implementations.  
  
### Providing Inline Code with SetScriptBuffer  
 To configure your custom functoid to use inline script:  
  
1. Call **AddScriptTypeSupport** with [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) to enable inline code and set the supported script type.  
  
2. Invoke **SetScriptBuffer** to set the code to use for the custom functoid. You will call this function three times with the `functionNumber` parameter for custom cumulative functoids and once for custom noncumulative functoids.  
  
3. Use **SetScriptGlobalBuffer** to declare any global variables that your inline code uses.  
  
4. Use **RequiredGlobalHelperFunctions** to indicate the helper functions that your custom inline functoid requires.  
  
   You can build your script by using StringBuilder or constants. One approach to writing script code is to write a custom referenced functoid first and, when all bugs are eliminated, convert it to inline by copying your functions into string constants.  
  
### Providing Inline Code with GetInlineScriptBuffer  
 If your custom inline functoid supports a variable number of parameters, you will override **GetInlineScriptBuffer**. To configure your custom functoid to use inline script:  
  
1. In the constructor, declare that your custom functoid has variable inputs by setting **HasVariableInputs** to `true`.  
  
2. In the constructor, call **AddScriptTypeSupport** with [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) to enable inline code and set the supported script type.  
  
3. Override **GetInlineScriptBuffer** to construct and return the code to use in the map for your custom functoid. Use the parameters to build the correct code by checking the `scriptType` and `numParams`. The final parameter, `functionNumber`, should be 0. This is because cumulative functions have a fixed number of inputs and do not use this mechanism.  
  
4. Use **SetScriptGlobalBuffer** to declare global variables that your inline code uses.  
  
5. Use **RequiredGlobalHelperFunctions** to indicate the helper functions that your custom inline functoid requires.  
  
   The following code fragment builds a C# function with the number of parameters passed in `numParams` but with no function body. To use this code fragment, copy the example to your solution and add code to do something with the parameters and return a value.  
  
```  
// Override GetInlineScriptBuffer  
protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
{  
    // Is this one of the supported script types?  
    if(ScriptType.CSharp == scriptType)  
    {  
        // Assume functionNumber == 0  
        StringBuilder builder = new StringBuilder();  
        // Function declaration   
        builder.Append("public string MyFunction("  
        // Declare parameters using numParams  
        for(int i=0; i<numParams; i++)  
        {  
            // Separate params with a comma  
            if(i > 0)  
                builder.Append(", ");  
            // Declare parameters, param0 to paramNUMPARAM  
            builder.Append("string param" + i.ToString());  
        }  
        builder.Append(")\n");  
        // Function body; process params as needed  
        builder.Append("{\n");  
        builder.Append("}\n");  
        // Return script  
        return builder.ToString();  
    }  
    // scriptType is unsupported  
    return string.Empty;  
}  
```  
  
## Testing an Inline Script  
 Testing is an important consideration in any development effort. Custom inline functoids can be challenging to test. To simplify the process, use one or both of the following techniques:  
  
-   Examine the XSLT of a map that uses the custom inline functoid.  
  
-   Verify the input and output of a map that uses the custom inline functoid.  
  
### Examine the XSLT of a Map That Uses the Custom Inline Functoid  
 This technique often reveals problems with logic or subtle syntax issues. It also helps you to understand what happens in the map.  
  
 To view the XSLT for a map:  
  
1.  From a Visual Studio BizTalk project, click the **Solution Explorer** tab, right-click a map that uses your custom inline functoid, and then click **Validate Map**.  
  
2.  Scroll the Output window to find the URL for the XSLT file. Press CTRL and click the URL to view the file.  
  
> [!NOTE]
>  Remember that any changes made to the XSLT file will not be reflected in your custom functoid.  
  
### Test a Map That Uses the Custom Inline Functoid  
 This tests whether the map and custom inline functoid work as expected.  
  
 To test a map:  
  
1. From a Visual Studio BizTalk project, click the **Solution Explorer** tab, right-click a map that uses your custom inline functoid, and then click **Test Map**.  
  
2. Scroll the Output window to find the URL for the output file. Press CTRL and click the URL to view the file.  
  
   You can check input and output values to verify that the map behaved as expected.  
  
## Example  
 The following example illustrates how to create a custom inline functoid for concatenating two strings. It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    /// <summary>  
    /// Performs a string concatenation using inline code.  
    /// </summary>  
    public class CustomStringConcatFunctoid : BaseFunctoid  
    {  
        public CustomStringConcatFunctoid()  
            : base()  
        {  
            //ID for this functoid  
            this.ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUSTOMSTRINGCONCATFUNCTOID_NAME");  
            SetTooltip("IDS_CUSTOMSTRINGCONCATFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUSTOMSTRINGCONCATFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUSTOMSTRINGCONCATFUNCTOID_BITMAP");  
  
            // Put this string handling function under the String   
            // Functoid tab in the Visual Studio toolbox for functoids  
            this.Category = FunctoidCategory.String;  
  
            // 2 required parameters, no optional parameters  
            this.SetMinParams(2);  
            this.SetMaxParams(2);  
  
            // Functoid accepts two inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            this.OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Declare support for CSharp inline function and  
            // pass the method implementation to the buffer  
            AddScriptTypeSupport(ScriptType.CSharp);  
            SetScriptBuffer(ScriptType.CSharp, GetCSharpBuffer());  
        }  
  
        private string GetCSharpBuffer()  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string ConCatStrings(string val1, string val2)\n");  
            builder.Append("{\n");  
            builder.Append("    return val2+val1;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
    }  
}  
```  
  
## See Also  
 [Using BaseFunctoid](../core/using-basefunctoid.md)   
 [Developing a Custom Referenced Functoid](../core/developing-a-custom-referenced-functoid.md)   
 [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md)