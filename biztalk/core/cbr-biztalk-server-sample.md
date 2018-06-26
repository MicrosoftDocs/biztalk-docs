---
title: "CBR (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: add16683-4090-4854-8d6e-923b58937e9d
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CBR (BizTalk Server Sample)
The CBR sample demonstrates using the **ExplorerOM** administrative objects to add and configure new send ports for content-based routing of BizTalk messages.  

## Prerequisites  

- This sample requires that the CBRSample be deployed by running setup.bat located in the \<*Samples Path*\>\Messaging\CBRSample directory.  

- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  

- The Windows PowerShell script example requires the Windows PowerShell execution policy to allow script execution. For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  

## What This Sample Does  
 This sample demonstrates using the administrative objects in the **Microsoft.BizTalk.ExplorerOM** namespace to add two new ports to the CBRApplication sample. These new ports are example ports for CBRApplication. The ports are configured to route messages to a hypothetical HTTP Web service address by using the HTTP adapter. The sample demonstrates the following operations using the **ExplorerOM** objects:  

-   Using the **AddNewSendPort** method of the **Application** class to add a new send port called SendportUSOrders to CBRApplication. The port is configured to use the HTTP adapter for transport with a hypothetical Web address.  

-   Adding a filter to SendportUSOrders that subscribes to messages in CBRApplication with the U.S. Country Code value of 100.  

-   Adding the CBRApplication map for transforming U.S.-based messages to the outbound maps for SendportUSOrders.  

-   Adding a new send port called SendportCANOrders to CBRApplication and configuring it to use the HTTP adapter for transport with a hypothetical Web address.  

-   Adding a filter to SendportCANOrders that subscribes to messages in CBRApplication with the Canada Country Code value of 200.  

-   Adding the CBRApplication map for transforming Canadian-based messages to the outbound maps for SendportCANOrders.  

## Where To Find This Sample  
 The sample is located in the following SDK location:  

 \<*Samples Path*\>\Admin\ExplorerOM\CBR  

 The following table shows the files in this sample and describes their purpose.  


|           File(s)            |                                                 Description                                                  |
|------------------------------|--------------------------------------------------------------------------------------------------------------|
|    ContentBasedRouting.cs    | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample. |
| CBR.sln, CBR.csproj, CBR.suo |                                  Solution and project files for the sample.                                  |

## Building and Running This Sample  

#### To build this sample  

1. Make sure you have completed the steps for building, deploying, and configuring the CBRSample. Those steps are provided in [CBRSample (BizTalk Server Sample)](../core/cbrsample-biztalk-server-sample.md).  

2. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file CBR.sln.  

3. On the **Build** menu, click **Build Solution**.  

#### To run this sample  

1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and navigate to the **CBRApplication** node.  

2. Expand the **CBRApplication** node to verify that the **Send Ports** node currently has only two ports listed as CBRUSSendPort and CBRCANSendPort.  

3. Open a command window and navigate to the following folder:  

    \<*Samples Path*\>\Admin\ExplorerOM\CBR\bin\Debug  

4. Run the file CBR.exe.  

5. Press F5 in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to refresh the view under the **Send Ports** node. You should now see the two new ports added to CBRApplication by this sample. They are called SendportUSOrders and SendportCANOrders.  

## Windows PowerShell Script Example  
 The following Windows PowerShell script can be used to demonstrate the same features of the **ExplorerOM** classes. However, because the **Add** method for the **SendPort.OutboundTranforms** collection is marked Internal in the **ExplorerOM** assembly it cannot be called directly from Windows PowerShell. This Windows PowerShell script demonstrates using the BizTalk WMI Provider from Windows PowerShell to add the outbound transform map to the new port.  

```  
Function WMI_AddOutboundTransformToPort($transform,$strPortName)  
{  
    Write-Host "WMI Processing Transform...`r`nPortName `:"$strPortName  
    Write-Host "Transform `:"$transform.AssemblyQualifiedName  

    $WMIsendport = get-wmiobject MSBTS_SendPort -filter "Name=`"$strPortName`"" -namespace root\microsoftbiztalkserver  
    $WMIsendport.OutboundTransforms = $transform.AssemblyQualifiedName  
    [Void] $WMIsendport.Put()  
    [Void] $WMIsendport.Start()  
}  

#===================#  
#=== Main Script ===#  
#===================#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

$CBRApp = $Catalog.Applications["CBRApplication"]  

if ($CBRApp -eq $null)  
{  
    Write-Host "`r`nFailed to find `"CBRApplication`" deployed on this BizTalk server."  
    Write-Host "You must deploy the SDK\Samples\Messaging\CBRSample in order to test this script.`r`n"  
}  
else  
{  
    #=== Register a trap handler for any exceptions ===#  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

    #===================================#  
    #=== Create the U.S. Orders Port ===#  
    #===================================#  

    $USPort = $CBRApp.AddNewSendPort($false,$false)  
    $USPort.Name = "SendportUSOrders"  
    $USPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $USPort.PrimaryTransport.Address = "http://process_orders_US.asp"  
    $USPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  

    #=== add the filter to subscribe to messages with U.S country code 100 ===#  

    $USPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='100'/>" +  
                     "</Group></Filter>"  

    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  

    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  

    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2USMap"] $USport.Name  

    #=====================================#  
    #=== Create the Canada Orders Port ===#  
    #=====================================#  

    $CanadaPort = $CBRApp.AddNewSendPort($false,$false)  
    $CanadaPort.Name = "SendportCANOrders"  
    $CanadaPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $CanadaPort.PrimaryTransport.Address = "http://process_orders_CAN.asp"  
    $CanadaPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  

    #=== add the filter to subscribe to messages with U.S country code 100 ===#  

    $CanadaPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='200'/>" +  
                     "</Group></Filter>"  

    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  

    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  

    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2CANMap"] $CanadaPort.Name  

    Write-Host  
}  
```  

 Here is an example output from running the Windows PowerShell script to create the two new ports. The new ports can also be verified in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console as mentioned above.  

```  
PS C:\> .\CBR.ps1  

Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportUSOrders  
Transform : CBRSample.CBRInput2USMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  

Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportCANOrders  
Transform : CBRSample.CBRInput2CANMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  

```  

## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)   
 [CBRSample (BizTalk Server Sample)](../core/cbrsample-biztalk-server-sample.md)