---
title: "SendPorts (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b84f96a2-b749-4fe0-be15-e4dd13eff66f
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendPorts (BizTalk Server Sample)
The SendPorts sample demonstrates how to enumerate and manage send ports by using the **Microsoft.BizTalk.ExplorerOM** administration classes.  

## Prerequisites  

- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  

- The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution. For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  

## What This Sample Does  
 This sample demonstrates using the **BtsCatalogExplorer** and **SendPort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage send ports in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. A Windows PowerShell example script is also included in this topic. The sample demonstrates the following operations:  

1. Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.  

2. Creating two new send ports named myStaticOnewaySendPort1 and myDynamicTwowaySendPort1. myStaticOnewaySendPort1, as its name implies, is a static one-way send port.  It is created to use the HTTP transport with an example destination URL http://sample1. myDynamicTwowaySendPort1 is created as a dynamic two-way send port.  

3. Enumerating send ports in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. This example enumeration should include the two new send ports.  

4. Deleting the two new send ports.  

5. Configuring the new send ports. The configurations demonstrated by the sample are applied to the example send port named myStaticOnewaySendPort1. The configurations applied by the sample include the following:  

   -   Enabling the **Request message before port processing** option for tracking message bodies.  

   -   Enabling the **Request message after port processing** option for tracking message bodies.  

   -   Specifying an encryption certificate for the send port to use on outgoing messages.  

   -   Specifying a filter for enlistment against a set of messages.  

   -   Adding a map to transform the messages.  

6. Changing send port status on the two new send ports.  The execution of the sample will make the following status changes on the myStaticOnewaySendPort1:  

   -   Change the status to started.  

   -   Change the status to stopped.  

   -   Change the status to bound. The bound status is the same as unenlisted.  

## Where To Find This Sample  
 The sample is located in the following SDK location:  

 \<*Samples Path*\>\Admin\ExplorerOM\SendPorts  

 The following table shows the files in this sample and describes their purpose.  


|                    File(s)                     |                                                 Description                                                  |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|                  SendPorts.cs                  | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample. |
| SendPorts.sln, SendPorts.csproj, SendPorts.suo |                                  Solution and project files for the sample.                                  |

## Building and Running This Sample  

#### To build this sample  

1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendPorts.sln.  

2. On the main menu, click **Build**, and then click **Build Solution**.  

#### To run this sample  

1.  Open a command window and navigate to the following folder:  

     \<*Samples Path*\>\Admin\ExplorerOM\SendPorts\bin\Debug  

2.  Run the file SendPorts.exe.  

## Windows PowerShell Script Example  
 The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:  

```  
Function CreateSendPorts($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  

    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

    #=== create a new static one-way send port using HTTP transport ===#  

    $myStaticOnewaySendPort = $Catalog.AddNewSendPort($false,$false)  
    $myStaticOnewaySendPort.Name = "myStaticOnewaySendPort1"  
    $myStaticOnewaySendPort.PrimaryTransport.TransportType = $catalog.ProtocolTypes["HTTP"]  
    $myStaticOnewaySendPort.PrimaryTransport.Address = "http://sample1"  
    $myStaticOnewaySendPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  

    #=== create a new dynamic two-way send port ===#  

    $myDynamicTwowaySendPort = $catalog.AddNewSendPort($true,$true)  
    $myDynamicTwowaySendPort.Name = "myDynamicTwowaySendPort1";  
    $myDynamicTwowaySendPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"];  
    $myDynamicTwowaySendPort.ReceivePipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLReceive"];  

    #=== Persist new ports to BizTalk configuration database ===#  

    Write-Host Adding $myStaticOnewaySendPort.Name...  
    Write-Host Adding $myDynamicTwowaySendPort.Name...  
    $catalog.SaveChanges();  
    Write-Host "`r`nCreateSendPorts() completed."  
}  

Function DeleteSendPorts($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  

    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

    #=== Delete this sample's new send ports by name ===#  

    $Catalog.RemoveSendPort($Catalog.SendPorts["myStaticOnewaySendPort1"])  
    $Catalog.RemoveSendPort($Catalog.SendPorts["myDynamicTwowaySendPort1"])  

    #=== Persist changes to BizTalk configuration database ===#  

    $catalog.SaveChanges();  
    Write-Host "DeleteSendPorts() completed."  
}  

Function EnumerateSendPorts($Catalog)  
{  
    #=== Display all send ports and their status info ===#  

    $catalog.SendPorts | format-table -Property Name, Status -autosize  

    Write-Host "EnumerateSendPorts`(`) completed."  
}  

Function ConfigureSendPort($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  

    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

    $sendport = $catalog.SendPorts["myStaticOnewaySendPort1"];  

    #=== specify tracking settings for tracking ===#  

    Write-Host $sendport.Name: Enabling BeforeSendPipeline and AfterSendPipeline message body tracking.  
    $sendport.Tracking = ([Microsoft.BizTalk.ExplorerOM.TrackingTypes] "BeforeSendPipeline" -bor   
                         [Microsoft.BizTalk.ExplorerOM.TrackingTypes] "AfterSendPipeline")  

    #=== specify an encryption certificate for outgoing messages ===#  

    Write-Host $sendport.Name: Adding a encryption certificate  
    foreach ($certificate in $catalog.Certificates)  
    {  
        if ($certificate.UsageType -eq [Microsoft.BizTalk.ExplorerOM.CertUsageType] "Encryption")  
        {  
            $sendport.EncryptionCert = $certificate  
        }  
    }  

    #=== specify filters for content-based routing ===#  
    Write-Host $sendport.Name: Adding a filter  
    $sendport.Filter = "<Filter><Group>" +  
                       "<Statement Property='SMTP.Subject' Operator='0' Value='Purchase Order'/>" +  
                       "<Statement Property='SMTP.From' Operator='0' Value='Customer'/>" +  
                       "</Group></Filter>"  

    #=== specify transform maps for document normalization ===#  

    foreach ($transform in $catalog.Transforms)  
    {  
        if (($transform.SourceSchema.FullName -ieq "myPO") -and (transform.TargetSchema.FullName -ieq "partnerPO"))  
        {  
            Write-Host $sendport.Name: Adding a transform  
            $sendport.OutboundTransforms.Add($transform)  
        }  
    }  

    #=== Persist all changes to BizTalk configuration database ===#  

    Write-Host $sendport.Name: Saving changes  
    $catalog.SaveChanges();  
    Write-Host "`r`nConfigureSendPort() completed."  
}  

Function ChangeSendPortStatus($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  

    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

    $sendport = $catalog.SendPorts["myStaticOnewaySendPort1"];  

    #=== start the send port to begin processing messages ===#  

    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Started"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  

    #=== stop the send port to stop processing and suspend messages ===#  

    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Stopped"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  

    #=== unenlist the send port to stop processing and discard messages ===#  

    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Bound"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)`(Unenlisted`)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
}  

#=== Main Script Body ===#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

#=== Exercise the CreateSendPorts function to create the two new ports ===#  

Write-Host "`r`n========================="  
Write-Host "=== CreateSendPorts`(`) ==="  
Write-Host "=========================`r`n"  
CreateSendPorts $Catalog  

#=== Enumerate all send ports to view the two new ports ===#  

Write-Host "`r`n============================"  
Write-Host "=== EnumerateSendPorts`(`) ==="  
Write-Host "============================`r`n"  
EnumerateSendPorts $Catalog  

#=== Add some configuration to the static send port ===#  

Write-Host "`r`n==========================="  
Write-Host "=== ConfigureSendPort`(`) ==="  
Write-Host "===========================`r`n"  
ConfigureSendPort $Catalog  

#=== Cycle through some status changes on the static send port ===#  

Write-Host "`r`n=============================="  
Write-Host "=== ChangeSendPortStatus`(`) ==="  
Write-Host "==============================`r`n"  
ChangeSendPortStatus $Catalog  

#=== Delete the two new ports ===#  

Write-Host "`r`n========================="  
Write-Host "=== DeleteSendPorts`(`) ==="  
Write-Host "=========================`r`n"  
DeleteSendPorts $Catalog  

Write-Host  
```  

 Here is example expected output from running the Windows PowerShell script sample.  

```  
PS C:\> & 'C:\SendPorts.ps1'  

=========================  
=== CreateSendPorts() ===  
=========================  

Adding myStaticOnewaySendPort1 ...  
Adding myDynamicTwowaySendPort1 ...  

CreateSendPorts() completed.  

============================  
=== EnumerateSendPorts() ===  
============================  

Name                      Status  
----                      ------  
ResendPort               Started  
HelloWorldSendPort       Started  
ToCustomerSendPort       Started  
CBRUSSendPort            Started  
CBRCANSendPort           Started  
SendportCANOrders          Bound  
myStaticOnewaySendPort1    Bound  
myDynamicTwowaySendPort1   Bound  

EnumerateSendPorts() completed.  

===========================  
=== ConfigureSendPort() ===  
===========================  

myStaticOnewaySendPort1 : Enabling BeforeSendPipeline and AfterSendPipeline message body tracking.  
myStaticOnewaySendPort1 : Adding a encryption certificate  
myStaticOnewaySendPort1 : Adding a filter  
myStaticOnewaySendPort1 : Saving changes  

ConfigureSendPort() completed.  

==============================  
=== ChangeSendPortStatus() ===  
==============================  

Changing myStaticOnewaySendPort1 status to Started ...  
Complete.  
Changing myStaticOnewaySendPort1 status to Stopped ...  
Complete.  
Changing myStaticOnewaySendPort1 status to Bound (Unenlisted)...  
Complete.  

=========================  
=== DeleteSendPorts() ===  
=========================  

DeleteSendPorts() completed.  
```  

## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)