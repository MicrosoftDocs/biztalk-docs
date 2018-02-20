---
title: "Function 0x43: Set V24 Output Status2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c8b4d92-5539-478a-8d6a-7faaf485d7b2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Function 0x43: Set V24 Output Status
This function allows the SNALink software to alter the modem output status on the adapter V.24 interface. There is no parameter or data packet on this request. The relevant V.24 settings are put into the driver interface record (see function 0x61) by the SNALink prior to calling the driver.  
  
## Return Values  
  
|IoStatus.Status|IoStatus.Information|  
|---------------------|--------------------------|  
|STATUS_DATA_ERROR|IO_ERR_HARDWARE_8273CMD_TIMEOUT|