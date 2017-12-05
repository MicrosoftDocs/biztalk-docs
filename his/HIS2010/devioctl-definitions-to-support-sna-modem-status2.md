---
title: "DevIoctl Definitions to Support SNA Modem Status2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 209ffda1-4bbf-41eb-a99e-f188568156a3
caps.latest.revision: 3
---
# DevIoctl Definitions to Support SNA Modem Status
The **SNA DevIoctl** interface is modified to update the [MODEM_STATUS](../HIS2010/modem-status2.md) structure for a link each time a modem status change is detected or caused by a **GetV24** or **SetV24** IOCTL call. Code is manually added to the link service to track the number of frames received and transmitted.  
  
 The **DevIoctl** changes are highlighted as follows.  
  
```  
#define SETV24STATUS                                              \  
         NtDeviceIoControlFile(seldrvrh,NULL,NULL,NULL,&IoStatus, \  
                               IoctlCodeSetV24,NULL,0L,           \  
                               &pInterfaceRecord->V24Out,1L);     \  
         if (SavedIROut != (InterfaceRecord.V24Out &              \  
                            (MASK_DTR | MASK_RTS)    ))           \  
         {                                                        \  
           SavedIROut = (pInterfaceRecord->V24Out &               \  
                         (MASK_DTR | MASK_RTS)    );              \  
           pSharedMem->V24Out = pInterfaceRecord->V24Out;         \  
         }  
  
#define GETV24STATUS(rc)                                          \  
         rc |= NtDeviceIoControlFile(seldrvrh,NULL,NULL,NULL,     \  
             &IoStatus,IoctlCodeGetV24,NULL,0L,NULL,0L);          \  
         rc |= READINTERFACERECORD;                               \  
         if (SavedIRIn != (InterfaceRecord.V24In &                \  
                     (MASK_CTS | MASK_DSR | MASK_DCD| MASK_DRI))) \  
         {                                                        \  
             SavedIRIn = (InterfaceRecord.V24In &                 \  
                     (MASK_CTS | MASK_DSR | MASK_DCD| MASK_DRI)); \  
             pSharedMem->V24In = InterfaceRecord.V24In;           \  
         }   
```  
  
 *pSharedMem* is a pointer to the [MODEM_STATUS](../HIS2010/modem-status2.md) structure for this link service.  
  
 *V24In* and *V24Out* are of type char and are used to notify the display application when status changes, not each time it is read or set.