---
title: "MSBTS_HostSetting.Name Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6d56e36-9b14-4279-817c-1bce936c2897
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.Name Property (WMI)
Contains the name of the BizTalk host.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string Name;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
 For sample code using the **MSBTS_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](../core/creating-updating-and-deleting-a-host-instance-using-wmi.md).  
  
## Example  
 The following example was taken from the SDK\Samples\Admin\WMI\Enlist Orchestration\CSharp\EnlistOrc.cs file.  
  
```csharp  
  
static void Main(string[] args)  
{  
   try  
   {  
      //Make sure the expected number of arguments were provided on the command line.  
      //If not, print usage text and exit.  
      if (args.Length != 2)   
      {   
         PrintUsage();                 
         return;  
      }  
  
      else  
      {  
         //set up a WMI query to acquire a list of orchestrations with the given Name and   
         //AssemblyName key values.  This should be a list of zero or one Orchestrations.  
         //Create the WMI search object.  
         ManagementObjectSearcher Searcher = new ManagementObjectSearcher();  
  
         Console.WriteLine("Got the args");  
  
         // create the scope node so we can set the WMI root node correctly.  
         ManagementScope Scope = new ManagementScope("root\\MicrosoftBizTalkServer");  
         Searcher.Scope = Scope;  
  
         string HostName = "";  
  
         // Build a Query to enumerate the MSBTS_Orchestration instances with the  
         // specified name and assembly name.  
         SelectQuery Query = new SelectQuery();      
         Query.QueryString = "SELECT * FROM MSBTS_HostSetting WHERE IsDefault ='TRUE'";  
  
         // Set the query for the searcher.  
         Searcher.Query = Query;  
         ManagementObjectCollection QueryCol = Searcher.Get();   
  
         foreach (ManagementObject Inst in QueryCol)  
         {  
            //Get the default host name.  
            HostName = Inst.Properties["Name"].Value.ToString();  
  
            Console.WriteLine("The Orchestration will be enlisted with the default host: " + HostName + ".");  
         }  
  
         // Build a Query to enumerate the MSBTS_Orchestration instances with the  
         // specified name and assembly name.  
         Query.QueryString = "SELECT * FROM MSBTS_Orchestration WHERE Name = '" + args[0]+ "' AND AssemblyName = '" + args[1] + "'";  
  
         // Set the query for the searcher.  
         Searcher.Query = Query;  
         QueryCol = Searcher.Get();   
  
         // Use a bool to tell if we enter the for loop  
         // below because Count property is not supported  
         bool OrchestrationFound = false;  
  
         foreach (ManagementObject Inst in QueryCol)  
         {  
            // There is at least one Orchestration  
            OrchestrationFound = true;  
  
            ManagementBaseObject inParams = Inst.GetMethodParameters("Enlist");  
            //Fill in input parameter values  
            inParams["HostName"] = HostName;  
  
            //Execute the method  
            ManagementBaseObject outParams = Inst.InvokeMethod("Enlist",inParams,null);  
            Console.WriteLine("The Orchestration was successfully enlisted.");  
         }  
  
         if(!OrchestrationFound)  
         {  
            Console.WriteLine("No Orchestration found matching that Name and AssemblyName.");  
         }  
      }  
   }  
  
   catch(Exception excep)  
   {  
      Console.WriteLine("An exception occurred " + excep.Message);  
      Console.WriteLine(excep.StackTrace);  
   }  
  
   Console.WriteLine("\r\n\r\nPress Enter to continue...");  
   Console.Read();  
}  
  
```  
  
 The following example was taken from the SDK\Samples\Admin\WMI\Enlist Orchestration\VBScript\EnlistOrch.vbs file.  
  
```vb  
  
Sub EnlistOrch()  
   'Get the command line arguments entered for the script  
   Dim Args: Set Args = WScript.Arguments  
  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   on error resume next  
  
   'Make sure the expected number of arguments were provided on the command line.  
   'if not, print usage text and exit.  
   If (Args.Count < 2) Or (Args.Count > 3) Then  
      PrintUsage()  
      wscript.quit 0  
   End If  
  
   Dim InstSet, Inst, Query, OrchestrationName, AssemblyName, HostName, Start  
  
   OrchestrationName = Args(0)  
   AssemblyName = Args(1)  
  
   'Check if orchestration is to be started  
   If (Args.Count = 3) Then  
      If ("Start" = Args(2)) Then  
         Start = True  
      Else  
         wscript.echo "Wrong optional flag."  
         PrintUsage()  
         wscript.quit 0  
      End If  
   End If  
  
   'set up a WMI query to acquire a list of defaul inprocess hosts  
   'This should be a list of zero or one host.  
   Query = "SELECT * FROM MSBTS_HostSetting WHERE IsDefault =""TRUE"""  
   Set InstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query)  
  
   'Check for error condition before continuing.  
   If Err <> 0 Then  
      PrintWMIErrorthenExit Err.Description, Err.Number  
   End If  
  
   'if Default Host found, get Host Name and NT Group Name.  There is only one default host.  
   If InstSet.Count > 0 Then  
      For Each Inst In InstSet  
         HostName = Inst.Name  
         If Err <> 0   Then  
            PrintWMIErrorthenExit Err.Description, Err.Number  
         End If  
         wscript.echo "Using default inprocess host " & HostName & "."  
      Next  
   End If  
  
   'set up a WMI query to acquire a list of orchestrations with the given Name and   
   'AssemblyName key values.  This should be a list of zero or one Orchestrations.  
   Query = "SELECT * FROM MSBTS_Orchestration WHERE Name =""" & OrchestrationName & """ AND AssemblyName = """ & AssemblyName & """"  
   Set InstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query)  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'If orchestration found, enlist the orchestration, otherwise print error and end.  
   If InstSet.Count > 0 then  
      For Each Inst in InstSet  
         Inst.Enlist(HostName)  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         wscript.echo "The Orchestration was successfully enlisted."  
  
         If Start Then  
            Inst.Start 2, 2  
            If Err <> 0   Then  
               PrintWMIErrorThenExit Err.Description, Err.Number  
            End If  
            wscript.echo "The Orchestration was successfully started."  
         End If  
      Next  
   Else  
      wscript.echo "No orchestration was found matching that Name and AssemblyName."  
   End If  
  
End Sub  
  
```  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.