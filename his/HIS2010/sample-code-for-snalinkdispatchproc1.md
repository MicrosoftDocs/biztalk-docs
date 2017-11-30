---
title: "Sample Code for SNALinkDispatchProc1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08e8c1c6-b979-4f72-a8b1-44ae13bf795a
caps.latest.revision: 3
---
# Sample Code for SNALinkDispatchProc
This section contains outline source code for the link dispatcher function [SNALinkDispatchProc](../HIS2010/snalinkdispatchproc1.md).  
  
```  
/**********************************************************************/  
/* First, include the SNA service header files                       */  
/**********************************************************************/  
#include <sna_dlc.h>  
#include <sna_cnst.h>  
#include <trace.h>  
  
/**********************************************************************/  
/* The link dispatcher routine - SNALinkDispatchProc                  */  
/**********************************************************************/  
VOID SNALinkDispatchProc (msgptr, function, locality)  
PTRBFHDR msgptr;  
INTEGER  function;  
INTEGER  locality;  
{  
  INTEGER     discard_buff;  
  COM_ENTRY("Ldisp");  
  if (msgptr != NULL)  
  {  
    TRACE4()"received message from local node"));  
    discard_buff = FALSE;  
    switch (msgptr->msgtype)  
    {  
      case OPENMSG:  
             /* process the OPEN message */  
             break;  
      case CLOSEMSG:  
             /* process the CLOSE message */  
             break;  
      case DLCDATA:  
             /* Data to be sent on link */  
             break;  
      case DLCSTAT:  
             /* Switch on the subtype of the message */  
             switch (msgptr->dshdr.dstype)  
             {  
               case STRESRCE :  
                      /* call flow control processor */  
                      break;  
               case DLCSDXID:  
                      /* call XID processor */  
                      break;  
               default:  
                      discard_buff = TRUE;  
                      break;  
             }  
             break;  
      default:  
             discard_buff = TRUE;  
             break;  
    }  
    if (discard_buff)  
    {  
      /* message has not been processed, so simply discard */  
      SNAReleaseBuffer(msgptr);  
      msgptr = NULL;  
    }  
  }  
  else if (function == SBLOST)  
  {  
    /* Lost contact with local node 'locality'  */  
    /* Terminate all connections on this node (matching destl-value) */  
  }  
  else if (function == SBTICK)  
  {  
    /* 5 second timer tick */  
  }  
  COM_EXIT;  
}  
  
```