---
title: "Developing a Custom Cumulative Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ea2c5fa-ed50-4b76-aee9-0d4adf9e6d8c
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing a Custom Cumulative Functoid
Use a custom cumulative functoid to perform accumulation operations for values that occur multiple times within an instance message.  
  
 You must implement three functions when developing a cumulative functoid. The three functions correspond to the initialize, cumulate, and get actions that the map needs to perform the accumulation. Before discussing these functions it is important to discuss thread safety.  
  
## Writing a Thread-Safe Functoid  
 The functoid code must be thread-safe because under stress conditions multiple instances of a map may be running concurrently. Some of the points to remember include:  
  
- Static state must be thread-safe.  
  
- Instance state does not always need to be thread-safe.  
  
- Design with consideration for running under high-stress conditions. Avoid taking locks whenever possible.  
  
- Avoid the need for synchronization if possible.  
  
  BizTalk Server provides a simple mechanism to reduce the complexity of writing a thread-safe cumulative functoid. All three functions have the same first parameter, an integer index value. BizTalk Server assigns a unique number to the index value when it calls your initialization function. You can use this value as an index into an array that holds accumulating values, as shown in the following code:  
  
```  
private HashTable cumulativeArray = new HashTable();  
…  
// Initialization function  
public string InitCumulativeMultiply(int index)  
{  
    cumulativeArray[index] = 1.0;  
    return string.Empty;  
}  
```  
  
 This example uses a HashTable instead of an ArrayList. This is because the initialization function might not be called with in-order index values.  
  
## Implementing the Three Cumulative Functions  
 You will need to implement three functions for each custom cumulative functoid you develop. The functions and the methods you must call in the constructor to set them are summarized in the following table. All of the functions return string values.  
  
> [!NOTE]
>  You determine the best name for each function, but each function must have the number and type of arguments specified.  
  
|Function Purpose|Arguments|To set a reference|To set inline script|  
|----------------------|---------------|------------------------|--------------------------|  
|Initialization|**int index**|**SetExternalFunctionName**|**SetScriptBuffer** with `functionNumber` = 0|  
|Cumulation|**int index, string val, string scope**|**SetExternalFunctionName2**|**SetScriptBuffer** with `functionNumber` = 1|  
|Get|**int index**|**SetExternalFunctionName3**|**SetScriptBuffer** with `functionNumber` = 2|  
  
### Initialization  
 Initialization enables you to prepare the mechanisms you will use to perform accumulation. You can initialize an array, reset one or more values, or load other resources as needed. The string return value is not used.  
  
### Cumulation  
 This is where you perform the accumulation operation appropriate for your functoid. BizTalk Server passes in the following three parameters:  
  
- **Index.** An integer value representing a map instance. There may be multiple map instances running concurrently.  
  
- **Val.** A string containing the value that should be accumulated. Unless you are writing a string Cumulate functoid it is a numeric value.  
  
- **Scope.** A string containing a number indicating which element or attribute value should be accumulated. Actual values are determined by an implementation.  
  
  You decide which values to accumulate and which values to ignore. For example, you may ignore values that are not below 0 but throw an exception when a value is not numeric. **BaseFunctoid** supplies two functions—**IsDate** and **IsNumeric**—to assist with validation.  
  
> [!NOTE]
>  If you use **IsDate** or **IsNumeric** in an inline script, be sure to set **RequiredGlobalHelperFunctions** so that the functions are made available to your script.  
  
 The string return value is not used.  
  
### Get  
 When BizTalk Server finishes iterating through all of the values determined by the functoid settings in the map, it requests the accumulated value. The get function has one argument, `Index`, which is an integer value representing a map instance. Your function should use the index value to find and return the accumulated value as a string.  
  
## Example  
 The following example illustrates how to create a custom functoid for performing cumulative multiplication. It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
using System.Collections;  
using System.Globalization;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    public class CumulativeMultiplyFunctoid : BaseFunctoid  
    {  
        private ArrayList myCumulativeArray = new ArrayList();  
  
        public CumulativeMultiplyFunctoid() : base()  
        {  
            //ID for this functoid  
            ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUMULATIVEMULTIPLYFUNCTOID_NAME");  
            SetTooltip("IDS_CUMULATIVEMULTIPLYFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUMULATIVEMULTIPLYFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUMULATIVEMULTIPLYFUNCTOID_BITMAP");  
  
            // Put this string handling function under the Cumulative  
            // Functoid tab in the Visual Studio toolbox for functoids  
            Category = FunctoidCategory.Cumulative;  
  
            // 2 required parameters, no optional parameters  
            SetMinParams(1);  
            SetMaxParams(2);  
  
            // Functoid accepts three inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType((~ConnectionType.FunctoidCount) & (~ConnectionType.FunctoidIndex) & (~ConnectionType.FunctoidIteration) & (~ConnectionType.FunctoidCumulative) & (~ConnectionType.FunctoidLooping) & (~ConnectionType.Record));  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Set the Initialize, Cumulative and Get functions  
            SetExternalFunctionName(GetType().Assembly.FullName, "Microsoft.Samples.BizTalk.CustomFunctoid.CumulativeMultiplyFunctoid", "InitCumulativeMultiply");  
            SetExternalFunctionName2("AddToCumulativeMultiply");  
            SetExternalFunctionName3("GetCumulativeMultiply");  
        }  
  
        // Initialization function  
        public string InitCumulativeMultiply(int index)  
        {  
            if (index >= 0)  
            {  
                if (index >= myCumulativeArray.Count)  
                {  
                    myCumulativeArray.Add(1.0);  
                }  
                else  
                {  
                    myCumulativeArray[index] = 1.0;  
                }  
            }  
  
            return "";  
        }  
  
        // Cumulative function  
        public string AddToCumulativeMultiply(int index, string val, string reserved)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            if (IsNumeric(val))  
            {  
                double dval = Convert.ToDouble(val, CultureInfo.InvariantCulture);  
                myCumulativeArray[index] = (double)(myCumulativeArray[index]) * dval;  
            }  
            return myCumulativeArray[index].ToString();  
        }  
  
        // Get Function  
        public string GetCumulativeMultiply(int index)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            return myCumulativeArray[index].ToString();  
        }  
    }  
```  
  
## See Also  
 [Using BaseFunctoid](../core/using-basefunctoid.md)   
 [Developing a Custom Inline Functoid](../core/developing-a-custom-inline-functoid.md)   
 [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md)