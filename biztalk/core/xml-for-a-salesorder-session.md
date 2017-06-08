---
title: "XML for a SalesOrder Session | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SalesOrder sessions"
  - "examples, SalesOrder session"
ms.assetid: dddf2424-b9d6-48a9-b7db-df524fafccd0
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML for a SalesOrder Session
The following sections provide samples of XML for a SalesOrder session.  
  
## BeginDoc XML Sample  
  
```  
<ns0:F4211FSBeginDoc xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CSALES/B4200310]">   
<ns0:mnCMJobNumber />  
<ns0:cCMDocAction>A</ns0:cCMDocAction>   
<ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
<ns0:szCMComputerID>BVISION02</ns0:szCMComputerID>   
<ns0:cCMUpdateWriteToWF>2</ns0:cCMUpdateWriteToWF>   
<ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>   
<ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>   
<ns0:szOrderType>SO</ns0:szOrderType>   
<ns0:szBusinessUnit>M30</ns0:szBusinessUnit>  
<ns0:szOriginalOrderCo />   
  
<ns0:szOriginalOrderNo />   
<ns0:szOriginalOrderType />   
<ns0:mnAddressNumber>1001</ns0:mnAddressNumber>   
<ns0:jdOrderDate />   
<ns0:szReference />   
<ns0:cApplyFreightYN>Y</ns0:cApplyFreightYN>  
<ns0:szCurrencyCode />   
<ns0:cWKSourceOfData />   
<ns0:cWKProcMode />   
<ns0:mnWKSuppressProcess>0</ns0:mnWKSuppressProcess>  
<ns0:cRetrieveOrderNo>1</ns0:cRetrieveOrderNo>   
<ns0:nSourceOfOrder>0</ns0:nSourceOfOrder>   
  
</ns0:F4211FSBeginDoc>  
  
```  
  
## EditLine XML Sample  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
  
<ns0:F4211FSEditLine xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CSALES/B4200310]">   
<ns0:mnCMJobNo>7</ns0:mnCMJobNo>   
<ns0:cCMLineAction>A</ns0:cCMLineAction>   
<ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
<ns0:cCMWriteToWFFlag>2</ns0:cCMWriteToWFFlag>   
<ns0:szCMComputerID>BVISION02</ns0:szCMComputerID>   
<ns0:szItemNo>210</ns0:szItemNo>   
<ns0:mnQtyOrdered>1</ns0:mnQtyOrdered>   
<ns0:cSalesTaxableYN>N</ns0:cSalesTaxableYN>  
<ns0:szTransactionUOM>EA</ns0:szTransactionUOM>   
<ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>   
<ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>   
<ns0:mnProcessID>4092</ns0:mnProcessID>   
<ns0:mnTransactionID>8</ns0:mnTransactionID>  
  
</ns0:F4211FSEditLine>  
  
```  
  
## EndDoc XML Sample  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
  
<ns0:F4211FSEndDoc xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CSALES/B4200310]">   
<ns0:mnCMJobNo>7</ns0:mnCMJobNo>   
<ns0:szCMComputerID>BVISION02</ns0:szCMComputerID>   
  
<ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>   
  
<ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>   
  
<ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
  
<ns0:mnProcessID>4092</ns0:mnProcessID>   
  
<ns0:mnTransactionID>8</ns0:mnTransactionID>  
</ns0:F4211FSEndDoc>  
  
```  
  
## See Also  
 [Appendix A: Sample Files](../core/appendix-a-sample-files.md)