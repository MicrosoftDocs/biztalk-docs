---
title: "Using IPv6 Addressing with BizTalk Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93cd2ead-5e87-47ac-8f78-d56b80afd34e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using IPv6 Addressing with BizTalk Adapters
BizTalk Server adapters support the use of IPv6 addressing. This topic describes the nomenclature that should be used to specify an IPv6 address for a UNC path, the nomenclature for specifying a literal IPv6 address, and the use of IPv6 scope identifiers with the HTTP and SOAP adapters.  
  
## IPv6 Address Nomenclature Used for a UNC Path  
 Follow these steps when specifying a literal IPv6 address in a UNC path:  
  
1. Replace any colon ":" characters with a dash "-" character.  
  
2. Append the text "**.ipv6-literal.net**" to the IP address.  
  
   For example, the nomenclature for a URI that points to a file share on a computer with the IPv6 address 2001:DB8:2a:1005:230:48ff:fe73:989d would be:  
  
```  
\\2001-DB8-2a-1005-230-48ff-fe73-989d.ipv6-literal.net\<sharename\>  
```  
  
 Where \<*sharename*\> is the name of the file share on the target computer.  
  
> [!NOTE]
>  Ensure that the user accounts for the host instances that the File send and receive handlers are running in have appropriate permissions to the file share. For more information about the folder permissions required to receive files with the File adapter see [Configure a File Receive Handler](../core/configure-the-file-adapter.md). For more information about the folder permissions required when sending files with the File adapter see [Known Issues with the File Adapter](../core/known-issues-with-the-file-adapter.md). For information about the file systems that are supported for use with the File adapter, see [http://support.microsoft.com/kb/815070](http://support.microsoft.com/kb/815070).  
  
## Using IPv6 Scope Identifiers with the HTTP Adapter and the SOAP Send Adapter  
 The HTTP send and receive adapter and the SOAP send adapter require that if a scope identifier is used in an IPv6 address, the scope identifier must be escaped with the escape code **%25**. For example, **fe80::550c:489f:e65e:aef3%8** is a valid IPv6 address containing a scope identifier (%8). To use this IPv6 address with the HTTP send and receive adapters or the SOAP send adapter, the scope identifier must be escaped as follows:  
  
```  
fe80::550c:489f:e65e:aef3%258  
```  
  
## Adapter URI Nomenclature Used for a Literal IPv6 Address  
  
-   To use a literal IPv6 address for an adapter URI, enclose the IP address in square brackets "[", "]". For example, the nomenclature for a URI with the IPv6 address 2001:DB8:2a:1005:230:48ff:fe73:989d would be:  
  
    ```  
    [2001:DB8:2a:1005:230:48ff:fe73:989d]  
    ```  
  
    > [!NOTE]
    >  The use of literal IPv6 addresses for adapter URIs follows the guidelines established in [RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375).  
  
-   When specifying a literal IPv6 address as the server name for the POP3 receive adapter, the SMTP send adapter, or the SQL send and receive adapters, the IPv6 address should not be enclosed in square brackets.  
  
## Summary of Considerations When Using Literal IPv6 Addressing with BizTalk Adapters  
 The table below summarizes when the use of a literal IPv6 address requires that the IP address is enclosed in square brackets "[", "]" and when a scope identifier that is used in an IPv6 address must be escaped:  
  
|Adapter|Requires that literal IPv6 address is enclosed in square brackets?|Requires that scope identifier is escaped?|  
|---|---|---|  
|POP3 receive|No|No|  
|SMTP send|No|No|  
|SQL send and receive|No|No|  
|File send and receive|No (see section **IPv6 Address Nomenclature Used for a UNC Path**)|No|  
|HTTP send and receive|Yes|Yes|  
|MQSeries send and receive|Yes|No|  
|MSMQ send and receive|Yes|No|  
|SOAP send|Yes|Yes|  
|SOAP receive|Yes|No|  
|WCF send and receive|Yes|No|