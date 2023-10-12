---
description: "Learn more about: Print Service Properties"
title: "Print Service Properties1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "snaprint_server"
---
# Print Service Properties
Click **No Event Log for Skipping Transparent Section** to prevent an entry in the Event Log every time print services skips a transparent section found while printing a host print job. Skipping transparent sections can be enabled from the **Advanced** tab of a print session properties page.  
  
 **3270**  
 Click **Flush Final FF** causes Host Print services to explicitly form feed the document at the end of a print job. This is not needed for most print jobs and configurations.  
  
 Click **Use Proportional Font Change** to prevent overlapping characters in documents containing nonfixed-type fonts printed through Host Print services. Most standard 3270 data streams are designated for fixed-type fonts.  
  
 Click **Ignore Characters 3F and Under** to cause the print service to ignore Hexadecimal characters 3F and below. In LU 1 data streams, this option causes hexadecimal characters below 40 to be replaced by spaces.  
  
 Click **Delay Print Start** to delay the start of the print job until printable data is received by Host Print services. In a few environments, hosts may poll the Host Print service for activity by sending "empty jobs". In such cases, not selecting this option may cause blank pages to be printed between actual print jobs.  
  
 **LU 3 Only**  
 Click **Do All FF** to force the printer driver to honor all form feed commands. (In most jobs, this is unnecessary and may lead to unwanted blank pages.)  
  
 Click **Always do NL** to insert a new line when the print services determines that the Maximum Print Position has been reached for a particular line of data. Selecting this option will prevent data from printing over an existing line.  
  
 Click **No Space After FF** to prevent print services from inserting a space character following a form feed.  
  
 Click **Support Embedded Printer Codes** to allow unmarked embedded characters, such as EBCDIC X'27' characters, to pass through print services to the printer.  
  
## LU 1 Only  
 Click **Use Fixed Tabs** to disable normal tab functionality (such as aligning tabs in columns) and interpret each tab as a fixed number of spaces. The number of spaces for a tab stop is based on the size of the first tab in the Set Horizontal Format SCS control code.  
  
 **APPC**  
 Set the **Activation Retry Limit** to the number of times print services will attempt to activate the APPC conversation following a terminated connection. The default value is –1 (infinite), meaning that attempts to activate the session will continue until it is successful or terminated manually.  
  
 Click **Infinite Retry Limit** to force the system to retry printing the job until it is successful.  
  
 Set the **Activation Retry Interval** to the number of seconds to wait before trying to print the job again. The default value is 10 seconds.  
  
## See Also  
 [Configuring Your Enterprise](../core/configuring-your-enterprise1.md)
