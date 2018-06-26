---
title: "ReceivePorts (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c403005d-5e0e-4015-b138-6318e03192af
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ReceivePorts (BizTalk Server Sample)
The ReceivePorts sample demonstrates how to create a new receive port by using the **ExplorerOM** administrative classes.  

## Prerequisites  

- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  

- The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution. For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  

## What This Sample Does  
 This sample demonstrates using the **BtsCatalogExplorer** and **ReceivePort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to add a new receive port to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. A Windows PowerShell example script is also included in this topic. The sample demonstrates the following operations:  

-   Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.  

-   Adding a new receive port by using the **AddNewReceivePort** method.  

-   Enumerating receive ports.  

-   Deleting receive ports.  

## Where To Find This Sample  
 The sample is located in the following SDK location:  

 \<*Samples Path*\>\Admin\ExplorerOM\ReceivePorts  

 The following table shows the files in this sample and describes their purpose.  


|                 File(s)                  |                                                 Description                                                  |
|------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|             ReceivePorts.cs              | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample. |
| ReceivePorts.sln and ReceivePorts.csproj |                                  Solution and project file for the sample.                                   |

## Building and Running This Sample  

#### To build this sample  

1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ReceivePorts.sln.  

2. On the **Build** menu, click **Build Solution**.  

#### To run this sample  

1.  Open a command window and navigate to the following folder:  

     \<*Samples Path*\>\Admin\ExplorerOM\ReceivePorts\bin\Debug  

2.  Run the file ReceivePorts.exe. The new receive port should be created and shown in the port enumeration. After the enumeration the receive port is immediately removed.  

## Windows PowerShell Script Example  
 The following Windows PowerShell example script can be used to demonstrate the same features of the **ExplorerOM** classes:  

```  
#==================================================================#  
#===                                                            ===#  
#=== Create a new receive port named "My Receive Port".         ===#  
#===                                                            ===#  
#==================================================================#  
Function CreateReceivePort()  
{   
  #=== Passing false here creates a one-way receive port opposed to a two-way ===#  
  $myreceivePort = $catalog.AddNewReceivePort($false)  

  $myreceivePort.Name = "My Receive Port"  
  $myreceivePort.Tracking = [Microsoft.BizTalk.ExplorerOM.TrackingTypes] "AfterReceivePipeline"  

  #=== Try to commit the changes made so far. If the commit fails, ===#  
  #=== roll back all changes.                                      ===#  
  $catalog.SaveChanges()  
}  

#===============================================================#  
#===                                                         ===#  
#=== Delete the receive port named "My Receive Port"         ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteReceivePort  
{  
  $receivePort = $catalog.ReceivePorts["My Receive Port"]  

  if ($receivePort -ne $null)  
  {  
    $catalog.RemoveReceivePort($receivePort)    

    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes in the trap handler.                  ===#  
    $catalog.SaveChanges()  
  }  
}  

#================================================================#  
#===                                                          ===#  
#=== Enumerate the receive ports.                             ===#  
#===                                                          ===#  
#================================================================#  
Function EnumerateReceivePorts  
{  
   #=== Enumerate the receive ports. ===#  
   foreach ($receivePort in $catalog.ReceivePorts)  
   {  
      Write-host "`r`n$($receivePort.Name)"  
   }  

   Write-host ""  
}  

#===================#  
#=== Main Script ===#  
#===================#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to delete the ===#  
#=== receive port.                                              ===#  
#==================================================================#  

$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding changes and continuing execution so we can attempt to clean up the receive port...`r`n"  
  $Catalog.DiscardChanges()  
}  

#=== Create the new receive port ===#  
Write-Host "`r`nAttempting to create `"My Receive Port`"..."  
CreateReceivePort  

#=== Enumerate each receive port ===#  
Write-Host "`r`nEnumerating all receive ports...`r`n"  
EnumerateReceivePorts  

#=== Prompt before removing the new example receive port ===#  
Write-Host "`r`nPress <ENTER> to delete `"My Receive Port`"..."  
Read-Host  
DeleteReceivePort  

#=== Enumerate again to show the receive port was removed ===#  
Write-Host "`r`nEnumerating all receive ports to show `"My Receive Port`" was removed...`r`n"  
EnumerateReceivePorts  

```  

 Here is an example of running the Windows PowerShell script to create the new receive port:  

```  
PS C:\> .\receiveports.ps1  

Attempting to create "My Receive Port"...  

Enumerating all receive ports...  

BatchControlMessageRecvPort  

ResendReceivePort  

HelloWorldReceivePort  

CBRReceivePort  

RP_ReceivePOFromInternal  

RP_ShipmentAgency1_OrderFiles  

RP_ShipmentAgency2_OrderFiles  

RP_ReceivePOFromBuyer  

RP_Receive_ShipmentAgency_Ack  

My Receive Port  

Press <ENTER> to delete "My Receive Port"...  

Enumerating all receive ports to show "My Receive Port" was removed...  

BatchControlMessageRecvPort  

ResendReceivePort  

HelloWorldReceivePort  

CBRReceivePort  

RP_ReceivePOFromInternal  

RP_ShipmentAgency1_OrderFiles  

RP_ShipmentAgency2_OrderFiles  

RP_ReceivePOFromBuyer  

RP_Receive_ShipmentAgency_Ack  
```  

## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)