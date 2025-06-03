---
description: "Learn more about: Sample InterAct and FileAct Messages"
title: "Sample InterAct and FileAct Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
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
  
