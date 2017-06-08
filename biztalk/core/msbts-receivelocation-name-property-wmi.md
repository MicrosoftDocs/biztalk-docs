---
title: "MSBTS_ReceiveLocation.Name Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c74b25d4-0d78-4160-aae2-2b00d270e1ae
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.Name Property (WMI)
Contains the name of the receive location.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```
string Name;  
```  
  
## Remarks  
 This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **ReceivePortName**, and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 128 characters.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceiveLocation.Name** property. 
  
## Example  
 The following example was taken from the SDK\Samples\Admin\WMI\Enumerate Receive Locations\VBScript\EnumRecLocs.vbs file.  
  
```vb  
  
Sub EnumRecLocs()  
  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   on error resume next  
  
   Dim InstSet, Inst  
   set InstSet = GetObject ("winmgmts:\root\MicrosoftBizTalkServer").InstancesOf("MSBTS_ReceiveLocation")  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'Report on number of receive locations found and list each one.  
   wscript.echo "A Total of " & InstSet.Count & " Receive Locations were found."  
   If InstSet.Count > 0 Then  
      For Each Inst In InstSet  
         wscript.echo  
         wscript.echo "Receive Location Name: " & Inst.Name  
         wscript.echo "  Disabled           : " & Inst.IsDisabled  
         wscript.echo "  Pipeline Name      : " & Inst.PipelineName  
         wscript.echo "  Receive Port Name  : " & Inst.ReceivePortName  
         wscript.echo  
      next  
   End If   
  
End Sub  
  
```  
  
 The following example was taken from the SDK\Samples\Admin\WMI\Enumerate Receive Locations\CSharp\EnumRLs.cs file.  
  
```csharp  
  
static void Main(string[] args)  
{  
   // Display help information   
   if (args.Length > 0)  
   {  
         if (args[0] == "/?")   
         {  
            Console.WriteLine();  
            Console.WriteLine();  
            Console.WriteLine("The correct usage of this sample is \"EnumRL.exe [RLName]\"");  
            Console.WriteLine("Where [RLname] is the name of a particular receive location to enumerate.");  
            Console.WriteLine("If receive location name contains spaces make sure to put it in quotes");   
            Console.WriteLine();  
            Console.WriteLine("Example #1 Enumerate all the receive locations.");  
            Console.WriteLine("         EnumRL");  
            Console.WriteLine();  
            Console.WriteLine("Example#2 enumerate just the \"My Receive Location #3\" receive location.");   
            Console.WriteLine("         EnumRL \"My Receive Location #3\" ");  
            Console.WriteLine();  
            Console.WriteLine();  
            Console.WriteLine("To get help use enumRL.exe /?");  
            return;  
         }  
   }  
  
   try   
   {     
      //Create the WMI search object.  
      ManagementObjectSearcher Searcher = new ManagementObjectSearcher();  
  
      // create the scope node so we can set the WMI root node correctly.  
      ManagementScope Scope = new ManagementScope("root\\MicrosoftBizTalkServer");  
      Searcher.Scope = Scope;  
  
      // Build a Query to enumerate the MSBTS_ReceiveLocation instances if an argument  
      // is supplied use it to select only the matching RL.  
      SelectQuery Query = new SelectQuery();   
      if (args.Length == 0)   
         Query.QueryString="SELECT * FROM MSBTS_ReceiveLocation";  
      else  
         Query.QueryString="SELECT * FROM MSBTS_ReceiveLocation WHERE Name = '" + args[0] + "'";  
  
      // Set the query for the searcher.  
      Searcher.Query = Query;  
  
      // Execute the query and determine if any results were obtained.  
      ManagementObjectCollection QueryCol = Searcher.Get();  
  
      // Use a bool to tell if we enter the for loop  
      // below because Count property is not supported  
      bool ReceiveLocationFound = false;  
  
      // Enumerate all properties.  
      foreach (ManagementBaseObject envVar in QueryCol)  
      {  
         // There is at least one Receive Location  
         ReceiveLocationFound = true;  
  
         Console.WriteLine("**************************************************");  
         Console.WriteLine("Receive Location:  {0}", envVar["Name"]);  
         Console.WriteLine("**************************************************");  
  
         PropertyDataCollection envVarProperties = envVar.Properties;  
         Console.WriteLine("Output in the form of: Property: {Value}");  
  
         foreach (PropertyData envVarProperty in envVarProperties)   
         {                 
            Console.WriteLine(envVarProperty.Name+ ":\t" + envVarProperty.Value);  
         }  
      }  
  
      if (!ReceiveLocationFound)   
      {  
         Console.WriteLine("No receive locations found matching the specified name.");  
      }   
   }  
  
   catch(Exception excep)  
   {  
      Console.WriteLine(excep.ToString());  
   }  
  
   Console.WriteLine("\r\n\r\nPress Enter to continue...");  
   Console.Read();  
}  
  
```  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.