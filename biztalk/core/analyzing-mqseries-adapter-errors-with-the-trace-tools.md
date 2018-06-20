---
title: "Analyzing MQSeries Adapter Errors with the Trace Tools | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Adapter Trace Utility, about Adapter Trace Utility"
  - "Adapter Trace Utility, installing"
  - "installing, Adapter Trace Utility"
  - "Adapter Trace Utility, enabling"
  - "errors, MQSeries adapters"
  - "MQSeries adapters, Adapter Trace Utility"
  - "Adapter Trace Utility, running"
  - "MQSeries adapters, errors"
  - "Adapter Trace Utility"
ms.assetid: fdc73d99-3b73-491d-9b2f-7064364fefa7
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Analyzing MQSeries Adapter Errors with the Trace Tools
You use the trace tools to analyze messaging failures when you run your application. With the MQSeries adapter you must use two tools, one for the adapter and your BizTalk application (trace.cmd), and the other for the MQSAgent (MQSTrace.cmd). Both tools use tracelog.exe. You have to install tracelog.exe if you do not already have it.  

 With both trace.cmd and MQSTrace.cmd you have to set an option (**-tools**) so that these tools can find the tracelog.exe file.  

## Install the Trace Utility  
 To install the BizTalk Adapter Trace Utility, follow these steps:  

1.  To download the Tracelog.exe file, visit the Microsoft Platform SDK download Web site at [http://go.microsoft.com/fwlink/?LinkId=21975](http://go.microsoft.com/fwlink/?LinkId=21975).  

2.  Start the Platform SDK Web installation program by clicking the link for the **PSDK-x86.exe** file at the bottom of the Web page.  

3.  When you are prompted, choose the option for a custom installation.  

4.  In the **Custom Installation** dialog box, click to clear all the available features.  

5.  Expand the **Microsoft Windows Core SDK** feature, and then expand the **Tools** feature.  

6.  Choose the **Tools (Intel 64-bit)** feature, and then click **Will be installed on local hard drive**.  

7.  Click **Next**, and then click **Next** again to start the installation.  

8.  Locate the *drive*:\\*MicrosoftPlatformSDKInstallationFolder\bin* folder, and then copy the Tracelog.exe file to the Microsoft BizTalk Server installation folder. The BizTalk Server installation folder also contains the Trace.cmd file.  

## Enable the Trace Utility  
 To enable the BizTalk Adapter Trace Utility in BizTalk Server, follow these steps:  

1.  Move to the directory that contains trace.cmd. The default location is the Microsoft BizTalk Server directory.  

2.  Type the following command, substituting the directory that contains the tracelog.exe file on your computer for the directory in quotes, and then press ENTER:  

     **trace -tools "c:\Program Files\Microsoft SDK\Bin"**  

3.  Move to the directory that contains MQSTrace.cmd.  

4.  Type the following command, substituting the directory that contains the tracelog.exe file on your computer for the directory in quotes, and then press ENTER:  

     **MQSTrace -tools "c:\Program Files\Microsoft SDK\Bin"**  

## Run the Trace Utility  
 To run the BizTalk Adapter Trace Utility, follow these steps:  

1. At the command prompt, type **trace.cmd -start -high**, and then press ENTER.  

2. Run your failure scenario.  

3. At the command prompt, type **trace.cmd -stop**, and then press ENTER.  

4. The bts2006.bin file contains the output of the trace tool. Contact Microsoft Product Support Services for analysis. For more information, see [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).  

   To run the MQSAgent Trace Utility, follow these steps:  

5. At the command prompt, type **MQSTrace.cmd -start -high**, and then press ENTER.  

6. Run your failure scenario.  

7. At the command prompt, type **MQSTrace.cmd -stop**.  

8. The MQSAdapterTrace.bin file contains the output of the trace tool. Contact Microsoft Product Support Services for analysis. For more information see [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).
