---
title: "Sample InterAct and FileAct Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8552167c-2acc-4eae-a86a-55ba2e54d4a2
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample InterAct and FileAct Messages
Samples of InterAct and FileAct real-time messages are given below.  
  
 **Sample InterAct real-time message**  
  
```  
<SwInt-ExchangeRequest>  
<SwInt-Request>  
<SwInt-RequestPayload>  
TestPayloadRequestSnF  
</SwInt-RequestPayload>  
</SwInt-Request>  
</SwInt-ExchangeRequest>  
```  
  
 **Sample FileAct real-time message (put request)**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Sw-ExchangeFileRequest>  
<Sw-FileRequest>  
<Sw-FileOpRequest>  
<Sw-PutFileRequest>  
<Sw-PhysicalName>%PhysicalFolderName%\sample_put.txt</Sw-PhysicalName>  
</Sw-PutFileRequest>  
</Sw-FileOpRequest>  
</Sw-FileRequest>  
</Sw-ExchangeFileRequest>  
```  
  
 **Sample FileAct real-time message (get request)**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Sw-ExchangeFileRequest>  
<Sw-FileRequest>  
<Sw-FileOpRequest>  
<Sw-GetFileRequest>  
<Sw-PhysicalName>%PhysicalFolderName%\sample_get.txt</Sw-PhysicalName>  
</Sw-GetFileRequest>  
</Sw-FileOpRequest>  
</Sw-FileRequest>  
</Sw-ExchangeFileRequest>  
```  
  
