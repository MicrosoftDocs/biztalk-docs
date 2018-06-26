---
title: "UnenlistParties (BizTalk Server Sample) | Microsoft Docs"
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
  - "parties, unenlisting"
  - "examples, administering"
  - "administering, examples"
ms.assetid: a751a0fc-ca94-4610-a8aa-db3a24159334
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# UnenlistParties (BizTalk Server Sample)
The UnenlistParties sample demonstrates how to unenlist all of the parties associated with a deployed BizTalk Server assembly.  
  
> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.  
  
## Prerequisites  
  
- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  
  
- The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution. For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## How This Sample is Designed and Why  
 This sample, written in Visual C# using objects from the BizTalk Explorer object model, performs the following operations:  
  
-   Query for a particular assembly.  
  
-   Retrieve all of the roles associated with that assembly.  
  
-   Unenlist all of the parties associated with each such role.  
  
-   Handle any errors such that meaningful information is returned to the user.  
  
## Where to Find This Sample  
 The sample is located in the following SDK location:  
  
 \<*Samples Path*\>\Admin\ExplorerOM\UnenlistParties\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs|Project, solution, and source files for building a Visual C# command-line application that unenlists all of the parties for a particular assembly.|  
  
### To build and initialize this sample  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file UnenlistParties.sln.  
  
2. In the **Build** menu, select **Build Solution**.  
  
### To run this sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Admin\ExplorerOM\UnenlistParties\bin\Debug\  
  
2. Run the file UnenlistParties.exe, passing one of the two following command-line arguments:  
  
   - **\<**
      ***AssemblyName* \>**. The name of an assembly from which all associated parties are to be unenlisted. If the assembly name contains spaces, enclose the name in quotes.  
  
   - **/?.** Displays help.  
  
     For example:  
  
   ```  
   UnenlistParties "My BizTalk Assembly.dll"  
   ```  
  
    -OR-  
  
   ```  
   UnenlistParties /?  
   ```  
  
## Windows Powershell Script Example  
 The following Windows Powershell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:  
  
```  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=====================================================#  
#=== If no assembly name is specified, just list   ===#  
#=== the assemblies, roles and partyies enlisted.  ===#  
#=====================================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`n===========================================================  
  Write-Host No assembly name provided for party unenlist operation.  
  Write-Host Listing Parties for each assembly on local BizTalk Server:  
  Write-Host ===========================================================`r`n  
  
  foreach ($assembly in $Catalog.Assemblies)  
  {  
    write-host $Assembly.Name`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
      write-host `t($role.name)  
  
      foreach($party in $role.EnlistedParties)  
      {  
        Write-Host `t`t($party.Party.Name)  
      }  
      write-host  
    }  
  }  
  
  write-host  
}  
  
#=====================================================#  
#=== If assembly name is specified, remove parties ===#  
#=== enlisted in all roles for the assembly.       ===#  
#=====================================================#  
  
else  
{  
  $Assembly = $Catalog.Assemblies[$args[0]]  
  
  if ($assembly -eq $null)  
  {  
    write-host Assembly named $args[0] not found.`r`n  
  }   
  
  else  
  {  
    write-host `r`nUnenlisting parties from all roles in ($Assembly.Name)`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
  
      $count = $role.EnlistedParties.count  
  
      for($c=0; $c -lt $count; $c++)  
      {  
        #==========================================================#  
        #=== Array index stays at zero because the collection   ===#  
        #=== changes after each item is removed.                ===#  
        #==========================================================#  
  
        $party = $role.EnlistedParties[0]  
  
        Write-Host Unenlisting ($party.Party.Name) from ($role.Name)...  
        $role.RemoveEnlistedParty($party)  
        Write-Host done.`r`n  
      }  
    }  
  
    write-Host Comitting changes...  
    $catalog.SaveChanges()  
    Write-Host done.`r`n  
  }  
}  
  
```  
  
 The following script output was generated from unenlisting parties from the Supplier assembly which is part of the PartyResolution sample. The PartyResolution sample is located in the \<*Samples Path*\>\Admin\Orchestrations\PartyResolution directory.  
  
```  
PS C:\> .\UnenlistParties.ps1 Supplier  
  
Unenlisting parties from all roles in Supplier  
  
Unenlisting ShipmentAgency1 from ShipmentRole ...  
done.  
  
Unenlisting ShipmentAgency2 from ShipmentRole ...  
done.  
  
Unenlisting BuyerAgency from Buyer ...  
done.  
  
Comitting changes...  
done.  
```  
  
## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)