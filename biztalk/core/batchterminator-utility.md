---
title: "BatchTerminator Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 771241fa-7df5-4882-8430-c2f36200cc9d
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BatchTerminator Utility
The BatchTerminator utility enables you to terminate all live batching orchestrations being used to batch EDI interchanges. This utility could prove useful if you have a large number of batching orchestration instances running, and you need to terminate all the batches in order to perform maintenance on the BizTalk server system.  
  
 The BatchTerminator utility is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator folder. When you run the utility to terminate the batching orchestration instances, the utility will log the results in the batchterminator.log file in the \<*drive*\>:\Documents and Settings\\<*user name*\>\Application Data folder.  
  
> [!NOTE]
>  The BatchTerminator utility is only supported on 32 bit systems.  BatchTerminator uses components in the Microsoft.BizTalk.ExplorerOM namespace, which is only supported if used from a 32 bit process.  
  
 **Restarting the Terminated Orchestration Instances**  
  
 After you terminate a group of batching orchestrations, you can do a bulk restart of those orchestration instances. You do so with the /Activate switch and the name and path of a file that indicates the batches that were stopped. When you run the utility to terminate a group of orchestration instances, the utility will create this stopped-batches file. The stopped-batches file is batchSettings-\<GUID\>.xml in the \<*drive*\>:\Documents and Settings\\<*user name*\>\Application Data folder. The path and name of the stopped-batches file is also saved in the log file. When the utility runs with the /activate switch, it validates the input file against a schema.  
  
 **Syntax**  
  
 Run the BatchTerminator utility in a command-line window with the following syntax:  
  
```  
BatchTerminator /<switch>  
```  
  
 You can run the BatchTerminator utility with the following switches. If no switch is provided, the /terminate option is used. As indicate below, you can enter the full name of the switch, such as /terminate, or the shortened form, in this case, /t.  
  
|||  
|-|-|  
|Switch|Function|  
|/?|Displays help|  
|/terminate -log:\<*log file*\><br /><br /> or /t -log:\<*log file*\>|Sends terminate control messages to all active X12 or EDIFACT batching orchestration instances. It displays the results of the operation, including a list of all active batch orchestration instances that it terminated, the number of active batch orchestrations that it found, and the number of terminate control messages that it sent. It logs the results into the batchterminator.log file in the \<*drive*\>:\Documents and Settings\\<*user name*\>\Application Data folder.<br /><br /> The optional -log: parameter enables you to specify the name of the log file and/or the path of the folder that you want the log file to be saved to. An example of using the parameter to specify the path and file name is the following: `BatchTerminator.exe /terminate -log:"C:\logs\log.txt"`. An example of using the parameter to specify the file name only is the following: `BatchTerminator.exe /terminate -log:log.txt`. If the path specified is invalid, the utility will use the default path: \<*drive*\>:\Documents and Settings\\<*user name*\>\Application Data. The -log: parameter can be used either with or without the /terminate switch.|  
|/print<br /><br /> or /p|Displays a listing of the current active batching orchestration instances without sending terminate control messages|  
|/activate:\<*path*\>\\<br />batchSettings-\<*GUID*\>.xml -log:\<*log file*\><br /><br /> or /a:\<*path*\>\\<br />batchSettings-\<*GUID*\>.xml -log:\<*log file*\>|Reactivates the previously terminated orchestration instances that are listed in the batchSettings-\<GUID\>.xml file. The utility will validate the input file against a schema embedded in the code. If the input file does not match the schema, an error message will be printed to the screen and the program will exit.<br /><br /> This operation writes information about the restarting action in the log file if you include the -log: switch.|  
  
 **Format of the Batch Activation File**  
  
 To reactivate previously terminated batch orchestration instances by using the /activate switch, you must provide a batch activation file (batchSettings-\<GUID\>.xml). This file must be in the following format:  
  
```  
<?xml version="1.0"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" elementFormDefault="qualified" id="BatchInfo" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="BatchTerminator">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Batch">  
          <xs:complexType>  
            <xs:attribute name="PartyName" type="xs:string" />  
            <xs:attribute name="PartyID" type="xs:int" use="required" />  
            <xs:attribute name=”BatchName” type=”xs:string” />  
            <xs:attribute name=”BatchID” type=”xs:int” use=”required” />  
            <xs:attribute name="EdiMessageType" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
-   You must be logged on as a member of the BizTalk Server Administrators group.  
  
### To run the BatchTerminator utility  
  
1. In Windows Explorer, move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator folder.  
  
2. Enter **BatchTerminator**, including any desired switches, and then click **Enter**.  
  
3. In Windows Explorer, move to \<*drive*\>:\Documents and Settings\\<*user name*\>\Application Data folder, and open the batchterminator.log file to see a log of the results.  
  
## See Also  
 [Utilities in the SDK](../core/utilities-in-the-sdk.md)