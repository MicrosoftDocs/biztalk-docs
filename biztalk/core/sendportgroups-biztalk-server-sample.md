---
title: "SendPortGroups (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4510aa31-16c3-475a-98aa-b590e13ae189
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendPortGroups (BizTalk Server Sample)
The SendPortGroups sample demonstrates how to enumerate and manage send port groups by using the **Microsoft.BizTalk.ExplorerOM** administration classes.  

## Prerequisites  

- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  

- The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution. For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  

## What This Sample Does  
 This sample demonstrates using the **BtsCatalogExplorer** and **SendPortGroup** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage send port groups in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. A Windows PowerShell example script is also included in this topic. The sample demonstrates the following operations:  

- Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.  

- Creating a new send port group named “My Send Port Group”.  

- Enumerating send port groups to display the newly created send port group.  

- Deleting the new send port group.  

  Additional functions are present in the sample but are not executed in the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] version.  Some of the additional functions are demonstrated in the PowerShell example script. The additional functions demonstrate the following functionality:  

- Adding a send port to the newly created send port group (covered in the PowerShell example).  

- Deleting a send port from the send port group (covered in the PowerShell example).  

- Starting the send port group.  

- Stopping the send port group.  

## Where To Find This Sample  
 The sample is located in the following SDK location:  

 \<*Samples Path*\>\Admin\ExplorerOM\SendPortGroups  

 The following table shows the files in this sample and describes their purpose.  


|                            File(s)                            |                                                 Description                                                  |
|---------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|                       SendPortGroups.cs                       | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample. |
| SendPortGroups.sln, SendPortGroups.csproj, SendPortGroups.suo |                                  Solution and project files for the sample.                                  |

## Building and Running This Sample  

#### To build this sample  

1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendPortGroups.sln.  

2. In Solution Explorer, double click **SendPortGroups.cs** to open the sample code.  

3. Find the `root.ConnectionString` in the `CreateSendPortGroup` function.  You must change the server specification to correctly point to the SQL server hosting your BizTalk Management database.  You can also use a period (.) to connect to the local SQL server.  For example:  

   ```  
   root.ConnectionString = "Integrated Security=SSPI;database=BizTalkMgmtDb;server=.";  
   ```  

4. Repeat step 3 for the following functions:  

   -   **EnumerateSendPortGroups**  

   -   **DeleteSendPortGroup**  

5. Save **SendPortGroups.cs**.  

6. On the main menu, click **Build**, and then click **Build Solution**.  

#### To run this sample  

1.  Open a command window and navigate to the following folder:  

     \<*Samples Path*\>\Admin\ExplorerOM\SendPortGroups\bin\Debug  

2.  Run the file SendPortGroups.exe.  

## Windows PowerShell Script Example  
 The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:  

```  
Function CreateSendPortGroup($Catalog, $strName)  
{  
   #=== Register a trap handler to discard changes on exceptions ===#  

   $ErrorActionPreference="silentlycontinue"  
   trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

   #=== Create a new send port group and set its name ===#  

   $NewSendPortGroup = $Catalog.AddNewSendPortGroup()  
   $NewSendPortGroup.Name = $strName  

   #=== Persist new ports to the BizTalk Management database ===#  

   Write-Host Adding "`"$($NewSendPortGroup.Name)`"..."  
   $catalog.SaveChanges();  
   Write-Host "`r`nCreateSendPortGroup() completed."  
}  

Function DeleteSendPortGroup($Catalog,$strName)  
{  
   #=== Register a trap handler to discard changes on exceptions ===#  

   $ErrorActionPreference="silentlycontinue"  
   trap { "Exception encountered DeleteSendPortGroup:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();}  

   #=== Delete this sample's new send ports by name ===#  

   $NewSendPortGroup = $Catalog.SendPortGroups[$strName]  
   $Catalog.RemoveSendPortGroup($NewSendPortGroup)  

   #=== Persist changes to the BizTalk Management database ===#  

   Write-Host "Deleting `"$strName`"..."  
   $catalog.SaveChanges();  
   Write-Host "DeleteSendPortGroup() completed."  
}  

Function EnumerateSendPortGroups($Catalog)  
{  
   #=== Register a trap handler to discard changes on exceptions ===#  

   $ErrorActionPreference="silentlycontinue"  
   trap { "Exception encountered During Enumeration:`r`n"; $_; "`r`n"}  

   #=== Display all send port groups by name ===#  

   $count = 1  
   foreach ($group in $catalog.SendPortGroups)  
   {  
     Write-Host "$count. $($group.Name)"  
     $count++  
   }  

   Write-Host "`r`nEnumerateSendPortGroups() completed."  
}  

Function PromptForSendPort($Catalog)  
{  
   #=== Provide a list of the send ports for the user to make a selection ===#  

   Write-Host "Here is a list of send ports:`r`n"  
   $count = 1  
   foreach($sendport in $Catalog.SendPorts)  
   {  
      Write-Host ($Count). ($Sendport.Name)  
      $count++  
   }     

   Write-Host "`r`nChoose a port to add to the group by ordinal (ex. 1,2, etc): " -nonewline  
   $selection = read-host  
   $selection = $Catalog.SendPorts[([int]$selection)-1]  
   Write-Host $Selection.Name selected.  

   return $Selection.Name     
}  

Function AddSendPortToSendPortGroup($Catalog,$strPortName,$strGroupName)  
{  

   #=== Add the user's selected send port to the group ===#  

   #========================================================#  
   #=== Presently, we have to use WMI from PowerShell    ===#  
   #=== This is because the methods on the collections   ===#  
   #=== are marked internal. So unfortunately the        ===#  
   #=== following very straightforward code won't work.  ===#  
   #========================================================#  

   # $sendportgroup = $Catalog.SendPortGroups[$strName]  
   # $sendportgroup.SendPorts.Add($Catalog.SendPorts[$strPortName])  
   # $catalog.SaveChanges();  

   #============================================================================#  
   #=== Get the WMI send port group representation to look up DB and server. ===#     
   #=== Expecting only one to match the query in this example.               ===#  
   #============================================================================#  

   $WQL = "select * from MSBTS_SendPortGroup where Name='" + $strGroupName + "'"  
   $groupset = gwmi -query ($WQL) -namespace "root\MicrosoftBizTalkServer"  

   #=== Create a new MSBTS_SendPortGroup2SendPort instance to map the port to the group ===#     

   $group2port = [WMICLASS]"root\MicrosoftBizTalkServer:MSBTS_SendPortGroup2SendPort"  
   $newPortEntry = [WMI] $group2port.psbase.CreateInstance()  
   $newPortEntry.MgmtDbServerOverride = $groupset.MgmtDbServerOverride   
   $newPortEntry.MgmtDbNameOverride = $groupset.MgmtDbNameOverride  
   $newPortEntry.SendPortGroupName = $groupset.Name  
   $newPortEntry.SendPortName = $strPortName  
   Write-Host "Adding $strPortName to $($groupset.Name)"  

   #=== Persist changes to the BizTalk Management database ===#  

   #=== POWERSHELL V1 BUG WORKAROUND =============================#  
   #=== First method call on a non-cimv2 WMI object can fail.  ===#  
   #=== The workaround in PowerShell V1 is to call GetType()   ===#  
   #=== as the first method.                                   ===#   
   $ErrorActionPreference="silentlycontinue"                     
   trap {}  
   $newPortEntry.GetType()  
   #=== POWERSHELL V1 BUG WORKAROUND =============================#  

   $ErrorActionPreference="continue"                     
   [void] $newPortEntry.Put()  

   #=== Since we used WMI to update the BizTalk Management database, ===#  
   #=== refresh our BtsExplorerCatalog to have an updated DB view.   ===#  

   $Catalog.Refresh()  
   Write-Host "AddSendPortToSendPortGroup() completed."  
}  

Function DeleteSendPortFromSendPortGroup($Catalog, $strPortName, $strGroupName)  
{  
   #========================================================#  
   #=== Presently, we have to use WMI from PowerShell    ===#  
   #=== This is because the methods on the collections   ===#  
   #=== are marked internal. So unfortunately the        ===#  
   #=== following very straightforward code won't work.  ===#  
   #========================================================#  

   # $sendportgroup = $Catalog.SendPortGroups[$strGroupName]  
   # $sendportgroup.SendPorts.Remove($Catalog.SendPorts[$strPortName])  
   # $catalog.SaveChanges();  

   #============================================================================#  
   #=== Get the WMI send port to group instance and delete it.               ===#     
   #=== Expecting only one to match the query in this example.               ===#  
   #============================================================================#  

   $WQL = "select * from MSBTS_SendPortGroup2SendPort where " +   
          "SendPortName='" + $strPortName + "' and " +   
          "SendPortGroupName='" + $strGroupName + "'"  

   $groupset = gwmi -query ($WQL) -namespace "root\MicrosoftBizTalkServer"  

   write-host "Removing $strPortName from $strGroupName..."  
   $groupset.Delete();  

   #=== Since we used WMI to update the BizTalk Management database, ===#  
   #=== refresh our BtsExplorerCatalog to have an updated DB view.   ===#  

   $Catalog.Refresh()  
   Write-Host "DeleteSendPortFromSendPortGroup() completed."  
}  

#========================#  
#=== Main Script Body ===#  
#========================#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "DATABASE=BizTalkMgmtDb;Integrated Security=SSPI;SERVER=."  

#=== Exercise the CreateSendPortGroup function to create a new send port group ===#  

$SendPortGroupName = "PowerShell Sample Send Port Group"  

Write-Host "`r`n============================="  
Write-Host "=== CreateSendPortGroup() ==="  
Write-Host "=============================`r`n"  
CreateSendPortGroup $Catalog $SendPortGroupName  

#=== Enumerate all send port groups to view the new one ===#  

Write-Host "`r`n================================="  
Write-Host "=== EnumerateSendPortGroups() ==="  
Write-Host "=================================`r`n"  
EnumerateSendPortGroups $Catalog  

#=== Add a send port to the group ===#  

Write-Host "`r`n===================================="  
Write-Host "=== AddSendPortToSendPortGroup() ==="  
Write-Host "====================================`r`n"  
$SendPortName = PromptForSendPort($Catalog)  
AddSendPortToSendPortGroup $Catalog $SendPortName $SendPortGroupName  

#=== Remove the send port from the group ===#  

Write-Host "`r`n========================================="  
Write-Host "=== DeleteSendPortFromSendPortGroup() ==="  
Write-Host "=========================================`r`n"  
DeleteSendPortFromSendPortGroup $Catalog $SendPortName $SendPortGroupName  

#=== Delete the group ===#  

Write-Host "`r`n============================="  
Write-Host "=== DeleteSendPortGroup() ==="  
Write-Host "=============================`r`n"  
DeleteSendPortGroup $Catalog $SendPortGroupName  

Write-Host  
```  

 Here is example expected output from running the Windows PowerShell script sample.  

```  
PS C:\> .\sendportgroups.ps1  

=============================  
=== CreateSendPortGroup() ===  
=============================  

Adding "PowerShell Sample Send Port Group"...  

CreateSendPortGroup() completed.  

=================================  
=== EnumerateSendPortGroups() ===  
=================================  

1. PowerShell Sample Send Port Group  

EnumerateSendPortGroups() completed.  

====================================  
=== AddSendPortToSendPortGroup() ===  
====================================  

Here is a list of send ports:  

1 . ResendPort  
2 . HelloWorldSendPort  
3 . ToCustomerSendPort  
4 . CBRUSSendPort  
5 . CBRCANSendPort  
6 . SendportCANOrders  

Choose a port to add to the group by ordinal (ex. 1,2, etc): 2  
HelloWorldSendPort selected.  
Adding HelloWorldSendPort to PowerShell Sample Send Port Group  
AddSendPortToSendPortGroup() completed.  

=========================================  
=== DeleteSendPortFromSendPortGroup() ===  
=========================================  

Removing HelloWorldSendPort from PowerShell Sample Send Port Group...  
DeleteSendPortFromSendPortGroup() completed.  

=============================  
=== DeleteSendPortGroup() ===  
=============================  

Deleting "PowerShell Sample Send Port Group"...  
DeleteSendPortGroup() completed.  
```  

## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)