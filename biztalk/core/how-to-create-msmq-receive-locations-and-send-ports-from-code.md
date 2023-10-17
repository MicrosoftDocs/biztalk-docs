---
title: "Create MSMQ Receive Locations and Send Ports from Code | Microsoft Docs"
description: Programmatically create MSMQ receive locations and send ports in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ebb4119-deeb-4287-aa65-7597ff0cc435
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create MSMQ Receive Locations and Send Ports programmatically
This topic explains how to use WMI to create a port or location for the MSMQ adapter.  
  
 For more information, see **Creating a Receive Location with a Datetime Schedule Configuration Using WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Setting Property Values  
 The process of creating a port or location is always the same:  
  
1. Create an object of the right type.  
  
2. Set the value of properties on the object.  
  
3. Commit the object values to the database.  
  
   All adapters have certain properties, such as **HostName**, in common. You set these common properties by directly assigning them to the object. The following C# code shows a typical case:  
  
```  
objReceiveLocation["HostName"] = "BizTalkServerApplication";  
```  
  
 You assign values to properties that not all adapters share. You create an XML document in a string and assign that string to the CustomCfg property. The following C# code shows a typical case for a FILE adapter:  
  
```  
objReceiveLocation["CustomCfg"] =   
        @"<CustomProps>"  
        + @"<BatchSize>20</BatchSize>"  
        + @"<FileMask>*.xml</FileMask>"  
        + @"<FileNetFailRetryCount>5</FileNetFailRetryCount>"  
        + @"<FileNetFailRetryInt>5</FileNetFailRetryInt>"  
        + @"</CustomProps>";  
```  
  
 The names of the tags in the CustomProps element are the internal names that the adapter uses for the properties.  
  
 The MSMQ adapter has a single tag, AdapterConfig, inside the CustomProps tag. The AdapterConfig tag contains a string of XML tags for the custom property values enclosed in a Config tag. However, the tags are encoded: "&lt;" replaces "\<" and "&gt;" replaces "\>". For example, the XML for a subset of the adapter for MSMQ properties might appear as follows:  
  
```  
<Config>  
    <batchSize>40</batchSize>  
</Config>  
```  
  
 Notice that the **vt** attribute is not used. The string assigned to the **CustomCfg** property appears as follows after encoding:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config><batchSize>40</batchSize></Config></AdapterConfig></CustomProps>  
```  
  
## Custom Property Names  
 The following table describes the internal names of the MSMQ adapter **Send** custom properties.  
  
|**Send custom property name**|**Display name**|  
|-----------------------------------|----------------------|  
|acknowledgeType|Acknowledgement Type|  
|administrationQueue|Administration Queue|  
|certificate|Certificate Thumbprint|  
|encryptionAlgorithm|Encryption Algorithm|  
|maximumMessageSize|Maximum Message Size (in KB)|  
|password|Password|  
|priority|Message Priority|  
|queue|Destination Queue|  
|recoverable|Recoverable|  
|segmentationSupport|Support Segmentation|  
|sendBatchSize|Batch Size|  
|sendQueueName|Destination Queue|  
|timeOut|Timeout|  
|timeOutUnits|Timeout Unit|  
|transactional|Transactional|  
|useAuthentication|Use Authentication|  
|useDeadLetterQueue|Use Dead Letter Queue|  
|useJournalQueue|Use Journal Queue|  
|userName|User Name|  
  
 The following table describes the internal names of the MSMQ adapter **Receive** custom properties.  
  
|**Receive custom property name**|**Display name**|  
|--------------------------------------|----------------------|  
|batchSize|Batch Size|  
|Password|Password|  
|Queue|Queue|  
|serialProcessing|Serial Processing|  
|Transactional|Transactional|  
|userName|User Name|  
  
## Sample Code  
 The following C# program creates a single receive location for the MSMQ adapter. It assumes that the receive port, ReceivePort1, exists and uses a helper function to encode and format the custom properties.  
  
```  
using System;  
using System.Management;  
using System.Text;  
  
namespace CreateReceive  
{  
    ///   
    /// Program to create a receive location.  
    ///   
    class CreateReceive  
    {  
        /// The main entry point for the application.  
  
        [STAThread]  
        static void Main()  
        {  
            // Custom properties & values  
            string cfg =   
                    @"<queue>FORMATNAME:DIRECT=OS:MYMACHINE02\PRIVATE$\QUEUE2</queue>"  
                    + @"<batchSize>40</batchSize>"  
                    + @"<transactional>true</transactional>"  
                    + @"<serialProcessing>false</serialProcessing>";  
  
            CreateReceiveLocation (  
                    "Code Created Location",  
                    "ReceivePort1",  
                    "MSMQ",  
                    "BizTalkServerApplication",  
                    EncodeCustomProps(cfg),  // Encode the custom props  
                    "Microsoft.BizTalk.DefaultPipelines.PassThruReceive,"   
                            + " Microsoft.BizTalk.DefaultPipelines,"   
                            + " Version=3.0.1.0, Culture=neutral,"   
                            + " PublicKeyToken=31bf3856ad364e35",  
                    @"FORMATNAME:DIRECT=OS:MYMACHINE\PRIVATE$\QUEUE2"  
                );  
  
        }  
  
        static string EncodeCustomProps (string cp) {  
  
            // Enclose the properties and values in a Config> tag.  
            StringBuilder tmp = new StringBuilder( @"<Config>" + cp + @"</Config>");  
  
            // Encode the string  
            tmp = tmp.Replace("<","<");  
            tmp = tmp.Replace(">",">");  
  
            return (  
                // Enclose the encoded string with necessary tags  
                "<CustomProps><AdapterConfig vt=\"8\">"  
                + tmp.ToString()   
                + "</AdapterConfig></CustomProps>");  
  
        }  
  
        static void CreateReceiveLocation (  
            string name,            // Location name  
            string port,            // Receive port, already exists  
            string adapterName,     // The transport type  
            string hostName,        // BTS host  
            string customCfg,       // Encoded custom properties  
            string pipeline,        // Full specification of pipeline  
            string inboundTransport)// Inbound transport url  
        {  
            try   
            {  
                // Create options to store options in management object  
                PutOptions options = new PutOptions();  
                options.Type = PutType.CreateOnly;  
  
                // Create a management object  
                // Get the class  
                ManagementClass objReceiveLocationClass =   
                           new ManagementClass(  
                               "root\\MicrosoftBizTalkServer",   
                               "MSBTS_ReceiveLocation",   
                               null);  
                // Create an instance of the member of the class  
                ManagementObject objReceiveLocation =  
                          objReceiveLocationClass.CreateInstance();  
  
                // Fill in the properties  
                objReceiveLocation["Name"] = name;  
                objReceiveLocation["ReceivePortName"] = port;  
                objReceiveLocation["AdapterName"] = adapterName;  
                objReceiveLocation["HostName"] = hostName;  
                objReceiveLocation["PipelineName"] = pipeline;  
                objReceiveLocation["CustomCfg"] = customCfg;  
                objReceiveLocation["IsDisabled"] = true;  
                objReceiveLocation["InBoundTransportURL"] = inboundTransport;  
  
                // Put the options -- creates the receive location  
                objReceiveLocation.Put(options);  
            }  
            catch (Exception excep)  
            {  
                System.Console.WriteLine("Create Receive Location ({0}) failed - {1}",  
                                                name, excep.Message);  
            }  
        }  
    }  
}  
```