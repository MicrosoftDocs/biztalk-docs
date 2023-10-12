---
description: "Learn more about: Sample Code: Initialization and Routing Procedure"
title: "Sample Code: Initialization and Routing Procedure1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Sample Code: Initialization and Routing Procedure
This topic contains an outline of source code for receiving messages from the Dynamic Access Module (DMOD).  
  
> [!NOTE]
>  TRACE*n*() is a macro used to specify data to be traced. This data can include variable parameters. The value **n** identifies the severity level of the trace. The unmatched parentheses are deliberate. They are resolved by the expansion of the macro.  
  
```  
/********************************************************************/  
/* Sample code for initialization and routing procedure.            */  
/********************************************************************/  
  
HSEM  dummysem = NULL;      /* This semaphore is never used         */  
  
/********************************************************************/  
/* Initialization procedure                                         */  
/********************************************************************/  
USHORT init_proc()  
{  
  COM_ENTRY("initp");  
  rc = sbpuinit(&dmodsem, CLIENT, CES3270, username);  
  TRACE4()"DMOD initialized, rc=%d",rc));  
  if (rc == NO_ERROR)  
  {  
  
    /********************************************************************/  
/* The procedure routproc will be called whenever a message is      */  
/* received by the DMOD. This is used to post back the application, */  
/* but take care to protect any queues against concurrent access by */  
/* multiple threads.                                                */  
/********************************************************************/  
    rc = sepdrout(routproc);  
    TRACE4()"Rout proc set up, rc=%d",rc));  
    if (rc == NO_ERROR)  
    {  
      /* Other initialization here                                  */  
    }  
  }  
  return (rc);  
}  
/********************************************************************/  
/* The routine routproc is called whenever the DMOD receives a      */  
/* message or a status indication.                                   */  
/********************************************************************/  
USHORT FAR _loadds routproc(buf, srcl, status)  
BUFHDR FAR *buf;        /* Buffer that has been received            */  
USHORT      srcl;       /* Locality from which buffer was received  */  
USHORT      status;     /* Reason for call                          */  
                        /* CEDINMSG = message received              */  
                        /* CEDINLLN = path error occurred (on srcl) */  
{  
  COM_ENTRY("routp");   /* initialize rc=FALSE                      */  
  
                        /* Call the DL BASE to handle re-resource   */  
                        /* location                                 */  
  if (!sbpurcvx(&buf, srcl, status))  
  {  
    switch (status) {  
      case CEDINMSG:  
        if (buf->destp == S3PROD)         /* Is the message for us? */  
        {  
          /********************************************************************/  
     /* Process the received message.                               */  
     /*                                                             */  
     /* If the message is DATAFMI on the PLU-SLU session, and the   */  
     /* application has requested to use flow control on the        */  
     /* session, then this processing should include:               */  
     /*                                                             */  
     /* -  increment number of messages received by the client      */  
     /* -  check whether the number received exceeds the threshold  */  
     /*    for normally returning credit to the node. If so, check  */  
     /*    whether it is OK to return credit (for example, not short of      */  
     /*    buffers), and if OK send a status-resource message to    */  
     /*    the node to give it credit to send more messages to the  */  
     /*    client.                                                  */  
/********************************************************************/  
          rc = TRUE;  
          TRACE2()"Routing proc got message at %p",buf));  
        }  
        else  
        {  
          TRACE2()"Routing proc did not take message at %p",buf));  
        }  
        break;  
  
      case CEDINLLN:  
        TRACE2()"Path error on %d",srcl));  
            /********************************************************************/  
        /* Process the path error status.                           */  
/********************************************************************/  
        break;  
    }  
  
    /********************************************************************/  
    /* If the message/status cannot be completely processed here,   */  
    /* the application can queue the message and clear a semaphore for the  */  
    /* main thread to continue the processing.                      */  
/********************************************************************/  
  } else {  
    rc = TRUE;       /* DLBase handled the message on our behalf    */<<<<<<<<<<This should be FALSE or Zero  
  }  
  /* Returning a value of TRUE indicates that we processed the      */  
  /* event return(rc);  
}  
  
Solution:  
A possible solution is to remove the else statment altogether.  
  
  Copy Code   
/********************************************************************/  
/* Sample code for initialization and routing procedure.            */  
/********************************************************************/  
  
HSEM  dummysem = NULL;      /* This semaphore is never used         */  
  
/********************************************************************/  
/* Initialization procedure                                         */  
/********************************************************************/  
USHORT init_proc()  
{  
  COM_ENTRY("initp");  
  rc = sbpuinit(&dmodsem, CLIENT, CES3270, username);  
  TRACE4()"DMOD initialized, rc=%d",rc));  
  if (rc == NO_ERROR)  
  {  
  
    /********************************************************************/  
/* The procedure routproc will be called whenever a message is      */  
/* received by the DMOD. This is used to post back the application, */  
/* but take care to protect any queues against concurrent access by */  
/* multiple threads.                                                */  
/********************************************************************/  
    rc = sepdrout(routproc);  
    TRACE4()"Rout proc set up, rc=%d",rc));  
    if (rc == NO_ERROR)  
    {  
      /* Other initialization here                                  */  
    }  
  }  
  return (rc);  
}  
/********************************************************************/  
/* The routine routproc is called whenever the DMOD receives a      */  
/* message or a status indication.                                   */  
/********************************************************************/  
USHORT FAR _loadds routproc(buf, srcl, status)  
BUFHDR FAR *buf;        /* Buffer that has been received            */  
USHORT      srcl;       /* Locality from which buffer was received  */  
USHORT      status;     /* Reason for call                          */  
                        /* CEDINMSG = message received              */  
                        /* CEDINLLN = path error occurred (on srcl) */  
{  
  COM_ENTRY("routp");   /* initialize rc=FALSE                      */  
  
                        /* Call the DL BASE to handle re-resource   */  
                        /* location                                 */  
  if (!sbpurcvx(&buf, srcl, status))  
  {  
    switch (status) {  
      case CEDINMSG:  
        if (buf->destp == S3PROD)         /* Is the message for us? */  
        {  
          /********************************************************************/  
     /* Process the received message.                               */  
     /*                                                             */  
     /* If the message is DATAFMI on the PLU-SLU session, and the   */  
     /* application has requested to use flow control on the        */  
     /* session, then this processing should include:               */  
     /*                                                             */  
     /* -  increment number of messages received by the client      */  
     /* -  check whether the number received exceeds the threshold  */  
     /*    for normally returning credit to the node. If so, check  */  
     /*    whether it is OK to return credit (for example, not short of      */  
     /*    buffers), and if OK send a status-resource message to    */  
     /*    the node to give it credit to send more messages to the  */  
     /*    client.                                                  */  
/********************************************************************/  
          rc = TRUE;  
          TRACE2()"Routing proc got message at %p",buf));  
        }  
        else  
        {  
          TRACE2()"Routing proc did not take message at %p",buf));  
        }  
        break;  
  
      case CEDINLLN:  
        TRACE2()"Path error on %d",srcl));  
            /********************************************************************/  
        /* Process the path error status.                           */  
/********************************************************************/  
        break;  
    }  
  
    /********************************************************************/  
    /* If the message/status cannot be completely processed here,   */  
    /* the application can queue the message and clear a semaphore for the  */  
    /* main thread to continue the processing.                      */  
/********************************************************************/  
  }   
  
  /* Returning a value of TRUE indicates that we processed the      */  
  /* event otherwise FALSE means the message was processed by */   
  /* DL - Base */  
  
return(rc);  
  
}  
  
```
