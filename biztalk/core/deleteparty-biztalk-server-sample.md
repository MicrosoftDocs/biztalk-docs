---
title: "DeleteParty (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, parties"
  - "parties, examples"
  - "deleting, parties"
  - "examples, administering"
  - "parties, deleting"
  - "administering, examples"
ms.assetid: 8161af7d-76ef-4df5-81c8-f0f5c81df9a8
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DeleteParty (BizTalk Server Sample)
The DeleteParty sample demonstrates how to delete a specified party.  
  
> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.  
  
> [!NOTE]
>  Before you can delete a party, you must first create one. One way to do this is to run the [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md) sample.  
  
## Prerequisites  
  
- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  
  
- The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution. For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## What This Sample Does  
 This sample, written in Microsoft Visual C#, using objects from the BizTalk Explorer object model (ExplorerOM), performs the following operations:  
  
-   Query for a specified party.  
  
-   Delete that party.  
  
-   Handle any errors such that meaningful information is returned to the user.  
  
## Where to Find This Sample  
 This sample is located in the following SDK location:  
  
 \<*Samples Path*\>\Admin\ExplorerOM\DeleteParty\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, DeleteParty.csproj, DeleteParty.sln, DeleteParty.cs|Project, solution, and source files for building a Visual C# command-line application that removes a specified party.|  
  
### To build and initialize this sample  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file DeleteParty.sln.  
  
2. On the **Build** menu, click **Build Solution**.  
  
### To run this sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Admin\ExplorerOM\DeleteParty\bin\Debug\  
  
2. Run the file DeleteParty.exe, passing one of the two following command-line arguments:  
  
   - **\<**
      ***PartyName* \>.** The name of a party to be deleted. If the party name contains spaces, enclose the name in quotes.  
  
   - **/?.** Displays help.  
  
     For example:  
  
   ```  
   DeleteParty "My Party #3"  
   ```  
  
    -OR-  
  
   ```  
   DeleteParty /?  
   ```  
  
## Windows Powershell Script example  
 The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:  
  
```  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=======================================#  
#=== If no party name is specified   ===#  
#=== just list the parties.          ===#  
#=======================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`nNo party name provided for delete operation.`r`n`r`nListing Parties on local Biztalk Server:  
  
  $Catalog.Parties | Format-List Name  
}  
  
#==========================================#  
#=== Delete the specified party by name ===#  
#==========================================#  
  
else  
{  
  $party = $Catalog.Parties[$args[0]]  
  Write-Host `r`nRemoving Party named `"($args[0])`"`r`n  
  $catalog.RemoveParty($party)  
  $catalog.SaveChanges()  
}  
```  
  
 The script example expects a single party name to be passed as a command line argument.  It looks for that party by name and attempts to delete it.  The script will list all parties on the local Biztalk server if no commandline argument is passed to it. Here is example output from the script:  
  
```  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party3  
  
Name : Party2  
  
PS C:\> .\DeletePart.ps1 Party3  
  
Removing Party named " Party3 "  
  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party2  
  
```  
  
## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)